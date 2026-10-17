<div align="center">

<img
src="https://github.com/user-attachments/assets/634dfa30-51da-4a3f-a93f-b973c10764f9"
width="155"
alt="WolfTube Logo"
/>

# WolfTube

### A Powerful YouTube Experience for iOS

**Downloads · Private Library · Playlists · Selective Backups · Background Playback · PiP · SponsorBlock · Shorts**

**Documented source baseline: v1.38.2 — Design Studio+ · Scoped Liquid Glass · iOS 27 Compatibility**

**Additional development work: Wolf Studio · RTL/UX improvements · 2160p playback validation · Shorts controls**

<br>

> 📦 Check the **Assets** section of [Releases](https://github.com/inc1x/WolfTube/releases) for published packages. The latest source version may be newer than the latest packaged release.
>
> ℹ️ Feature availability depends on the YouTube build, iOS version, and installation environment. Source-level checks are not a substitute for building and testing on a device.
>
> 🧪 The Wolf Studio/UX changes described below were developed on a **v1.36.21-based working branch**. The README also retains a **v1.38.2 source baseline**; these are distinct code snapshots, **not proof that the newer features are merged into v1.38.2 or available in a release**.

</div>

---

# ✨ About WolfTube

WolfTube is an advanced enhancement for YouTube on iOS that adds powerful media, playback, library, customization, and productivity features directly inside the YouTube application.

It is designed to feel integrated with YouTube rather than operating as a separate application.

WolfTube allows users to download media, maintain a personal offline library with optional Private access, create playlists with custom artwork, control playback, export selected content, manage multiple media items, and customize YouTube-integrated tools. Its interface preserves the white-wolf identity and Signature wordmark while offering **Classic** and **Studio** appearances for WolfTube-owned feature pages. Player and Shorts overlays continue to use their existing translucent **Liquid Glass** presentation.

---

# 🧪 Recent Development Work — Wolf Studio & UX (v1.36.21-based branch)

The following changes describe work carried out in a separate development branch. They are **source-level changes and intended behaviors**, not a guarantee of successful compilation, 4K playback on every device, or compatibility with all YouTube builds.

### 🐺 Wolf Studio — Customization Workspace

* **Dedicated Wolf Studio entry:** access appearance tools from WolfTube's main settings; redundant Studio shortcuts in Downloads and Appearance were removed.
* **Organized editing areas:** download indicator, player, Shorts, interface, and colors, rather than one long mixed settings list.
* **Component-linked live preview:** the download preview uses the actual `WTDownloadProgressCard` UI component and responds to supported changes in size, style, color, and simulated progress. Other preview scenes for player, Shorts, and interface illustrate settings but are **not live YouTube playback sessions**.
* **Flexible color gradients:** add, remove, and reorder up to 12 color stops on supported progress components; adjust indicator background and text colors where implemented.
* **Shape and dimension controls:** tune circular indicator size, progress bar width and thickness, ring thickness, edge style, and available tab-selection styling.
* **Custom looks:** save and restore up to eight personalized style presets in the development implementation.
* **Additional component options:** supported dynamic glass, selected-tab accent/animation, library glass sections, mini-player and Shorts-added progress line settings.
* **Language and RTL:** Studio reads the selected WolfTube language, with layout adjustments for Arabic. Not every string is guaranteed translated in every build.

### ✨ Interaction & Motion

* **Glass-style dialogs:** supported Studio save/reset and choice dialogs use WolfTube's translucent dialog presentation instead of standard alerts where wired up; iOS versions without the newest glass materials use compatible blur.
* **Motion tuning:** revised appearance/disappearance timings and transitions in supported WolfTube UI, with accessibility Reduce Motion respected where implemented.
* **Settings-exit prompt:** when preferences have changed during the settings session, exiting the main settings screen can offer **Not now** or **Close YouTube to apply changes**. Confirming starts a short fade before process exit; the user then opens YouTube manually. This is **not** a seamless OS-controlled restart and does not apply to every preference.
* **No unnecessary restart prompt:** merely browsing settings does not trigger the prompt.

### 🎬 Player, Shorts & 2160p

* **Video-only ad handling in the v1.36.21 work branch:** invasive Home/Feed ad filtering is disabled to avoid blank or missing video entries, while supported in-player advertisement controls remain best-effort. This change should not be read as applying automatically to the distinct v1.38.2 baseline.
* **Optional player overlays:** hide supported in-player recommendations and end-screen cards independently, without removing items from the main Home/Search feeds. This does **not** claim to hide every recommendation listed below a video.
* **Shorts tools:** separate Shorts long-press behavior from the standard video player's gesture choice; add a separate WolfTube button-visibility setting and a fallback handling path for supported Shorts layouts.
* **2160p compatibility checks:** prefer compatible codecs when equivalent 2160p streams are available; check video-frame decode after merging audio and video; try another same-resolution stream when supported. If no decodable result exists, report a failure rather than quietly treating an audio-only result as a successful 4K video. **4K support still depends on the device, codec and source streams.**
* **Shorts progress display:** the optional WolfTube-added progress line can be styled or hidden without removing YouTube's native seek controls.

### 🧹 Scope and Stability

* **Crash Logs:** the WolfTube crash-log viewer, export path, and background WolfTube logging are disabled in the user-facing development source; linking compatibility stubs remain as needed.
* **Native YouTube UI stays native:** Studio customizes WolfTube-owned surfaces; it does not intentionally redesign the YouTube Feed, native playback scrubber, or core navigation hierarchy.
* **Validation limits:** source checks and static regressions were reported for selected areas. **A complete Theos build and iOS 18/26/27 on-device test remain required.**

---

# 🆕 What's New — v1.38.2

**This section documents the v1.38.2 source baseline**, rather than the later-described v1.36.21-based Wolf Studio working branch. **Design Studio+** expands the appearance controls introduced in the 1.37–1.38 series while keeping WolfTube's playback overlays visually consistent with YouTube.

### 🎨 Design Studio+ & Live Preview

* **Two selectable looks:** **Classic** retains the previous WolfTube appearance; **Studio** provides a restrained graphite interface with carefully placed accent color for WolfTube settings and feature screens.
* **Live Preview:** preview the WolfTube Signature header, playlist styling, feature-row density, download button, and floating download indicator before committing changes.
* **Progress indicator colors:** choose **Red**, **White**, or **Gold** for WolfTube's download-progress bar/ring.
* **Progress indicator thickness:** choose **Thin**, **Balanced**, or **Bold**, with an interactive preview percentage slider.
* **Row density:** switch between the default and a more compact layout for WolfTube-owned settings and feature lists.
* **Existing indicator options:** choose the download indicator style, position, and animation from the same studio.
* **Review before applying:** changes are staged. Leaving the studio with edits offers **Apply**, **Discard**, or **Continue editing**. Resetting the preview does not immediately overwrite saved settings.
* **Refined settings UX:** Studio uses cleaner continuous rows and subtle dividers, rather than placing a colored card behind every item.

### 🫧 Design Scope & Playback Compatibility

* **Studio stays inside WolfTube features:** Quick Settings, feature pages, supported library and playlist views, and the Signature header can follow the selected appearance.
* **Liquid Glass stays in the player:** the WolfTube action menu over a YouTube video, media download sheet, player/Shorts buttons, and relevant playback overlays keep their existing glass or translucent treatment, regardless of whether Classic or Studio is selected.
* **Download-progress customization changes the indicator itself**, not the surrounding glass material or YouTube's native video timeline.
* **Shorts tab-bar refinements:** fixes target the Shorts-specific floating tab appearance and optional WolfTube-added progress line. Some visual differences remain dependent on the installed YouTube build and need on-device verification.

### 🧹 Release Cleanup & Stability

* **Crash Logs removed from the user interface:** WolfTube's old crash-log viewer, export action, automatic session logging, and custom crash handlers have been disabled in the normal app source. Developer-only Frida scripts remain in the repository and are not run as an in-app service.
* **Independent iOS 27 stability guards remain:** conservative Feed and collection-view handling is intended to prevent the earlier crashes and blank-feed regressions without aggressively modifying YouTube's layout or playback requests.
* **Local audio playback improvements:** the audio player supports a visible progress timeline with elapsed/remaining time and seeking where supported.
* **Source regression checks:** dedicated checks cover the new studio settings, design scoping, and selected iOS 27 compatibility paths.

> **Verification status:** v1.38.2 is a **source update**. The supplied project checks passed for the covered paths, but compilation with a particular Theos/iOS SDK and real-device behavior—especially on iOS 27—must be verified separately. An installed release may behave differently from the current source tree.

---

# 📥 Video & Audio Downloads

WolfTube adds a complete media downloading system directly into YouTube.

### Video Downloads

* Download videos directly from YouTube.
* Choose between multiple available video qualities.
* Support for high-resolution downloads when available, subject to codec and device playback compatibility.
* On the v1.36.21-based UX branch, 2160p downloads are checked for playable video frames after merging; available alternatives at the same resolution can be tried before a failure is reported. A successful transfer alone does not guarantee the iPhone can decode its video.
* Use supported direct media links for downloads.
* View download progress directly inside WolfTube.
* Choose a preferred download preset, quality, and destination in the download sheet.
* Save supported media to WolfTube's library or the Photos app.
* Use the download queue and scheduling controls when supported.
* Keep downloaded content organized inside the built-in library.

### Audio Downloads

* Download audio-only versions of supported videos.
* Use supported direct media links when available.
* Listen to downloaded audio offline.
* Play downloaded audio directly inside WolfTube.
* Add downloaded audio to custom playlists.

### Thumbnail Downloads

* Download video thumbnails.
* Retrieve high-quality thumbnail images.
* Save or share thumbnails using the native iOS share interface.

### Download Sheet & Floating Progress Indicator

The unified download sheet offers Video/Audio switching, expandable quality and preset choices, destination selection, and a fixed download action button. Its Arabic layout reserves separate space for icons and labels to avoid overlap. Active selections use a restrained translucent burgundy accent.

The floating download progress indicator supports multiple styles and positions, dragging to reposition where enabled, and an available cancel control. In the **v1.38.2 baseline**, Design Studio+ offers **Red / White / Gold** accents and **Thin / Balanced / Bold** thickness controls. The separate **Wolf Studio development branch** extends this to custom multi-stop gradients, indicator size, bar width, ring thickness, background/text colors, and additional shapes. Its download preview uses the real indicator UI component; production behavior still requires device testing. The enclosing Liquid Glass surface and YouTube's native video timeline remain separate from this customization.

### Direct Link Downloading

WolfTube uses direct media links for supported downloads and keeps download-related logic separated from normal YouTube playback as much as possible.

This improves compatibility and reduces unnecessary dependency on internal SABR download paths.

---

# 📚 Built-In Media Library

WolfTube includes a complete media library directly inside YouTube.

Downloaded content can display useful information such as:

> • Media title
> • Download quality
> • File size
> • Download date
> • Media type
> • Download progress
> • Playback progress

From the library, users can:

* Play downloaded videos.
* Play downloaded audio.
* Share downloaded files.
* Save supported media.
* Delete downloaded media.
* Search the library.
* Organize content using playlists.
* Resume media from the previous playback position.
* Edit local metadata such as title, channel/artist name, category, notes, and artwork without changing the underlying media file.
* Pin individual media items and organize them in optional library sections.
* Move selected items to the Private Library, where supported.
* Use dedicated **Recently Played** and other optional library sections.
* Trim supported downloaded video clips and share/save the result while preserving the original file.

---

# 🔐 Private Library & Custom Library Sections

WolfTube can keep supported downloaded items in a **Private** section. Entering Private is designed to require iOS authentication (Face ID, Touch ID, or the device passcode), rather than storing a separate WolfTube PIN.

In **Library & Interface**, users can request authentication at each new entry or configure a 1-, 5-, 15-, or 30-minute grace period. Returning from the background or leaving the Private section resets access according to the implemented lock behavior. An ordinary library refresh should not open Private or trigger authentication.

The **Customize Library** screen lets users show, hide, or reorder optional sections including Shorts, Recently Played, and Private. Videos, Songs, and Playlists remain core sections. The editing and selection sheets use lighter Liquid Glass-style surfaces with reduced gray overlays.

---

# ✅ Multi-Select

WolfTube includes a dedicated selection mode for managing multiple downloaded files at the same time.

Users can select multiple videos or audio files and clearly see which items are currently selected.

Supported batch actions include:

> • Share multiple files at once
> • Delete multiple files at once
> • Manage several library items together

This makes managing large offline libraries much faster.

---

# 🎶 Playlists

WolfTube allows users to create their own offline media collections directly inside YouTube.

Playlist features include:

* Create custom playlists.
* Add downloaded videos.
* Add downloaded audio.
* Mix video and audio inside the same playlist.
* Rename playlists.
* Pin favorite playlists.
* Keep pinned playlists at the top.
* Search playlists.
* Share playlists with other WolfTube users.
* Delete playlists.
* Undo accidental playlist deletion.
* Configure how artwork is chosen when a new playlist is created.
* Set a custom playlist image from the iOS Photo Library.
* Change playlist artwork at any time.
* Remove custom playlist artwork and restore the default WolfTube icon.
* Choose between Sequential, Repeat Current Track, and Shuffle playback modes.

### 🖼️ Custom Playlist Artwork

WolfTube allows users to replace the default playlist icon with a custom image selected directly from the iOS Photo Library.

Custom artwork is displayed in the playlist library and inside the playlist screen.

Users can:

> • Select an image from Photos
> • Replace the current playlist artwork
> • Remove custom artwork
> • Restore the default playlist icon

Custom playlist artwork is stored locally and can also be preserved through WolfTube Backup & Restore when the relevant playlist data is included.

### Artwork Prompt When Creating a Playlist

The **New playlist artwork** setting offers three modes: **Ask every time**, **Open Photos automatically**, or **Always use the default artwork**. If the user cancels photo selection, the playlist itself remains created with its default cover. This also applies when creating a playlist from an **Add to playlist** action.

### 🔁 Playlist Playback Modes

WolfTube includes multiple playlist playback modes:

> • Sequential
> • Repeat Current Track
> • Shuffle

**Sequential** plays playlist items in their normal order.

**Repeat Current Track** automatically restarts the currently playing item when it finishes.

**Shuffle** plays playlist items in a randomized order.

Playback mode changes are applied directly to the active playlist session. The updated playlist screen uses a softer translucent red glow for the current mode, rather than an opaque red selection block.

The playlist header also includes **Play all** and **Add audio** actions. Its detail view intentionally omits the old **Search this playlist** field; search remains available in the wider library and the **Select media** picker.

Playback controls also preserve their intended behavior in right-to-left languages such as Arabic.

### ⏪ Undo Playlist Deletion

After deleting a playlist, WolfTube temporarily allows the action to be undone to help prevent accidental data loss.

---

# 🔎 Library Search

WolfTube includes a fast search system for locating downloaded content.

Users can search through:

* Videos.
* Audio files.
* Playlists.
* Media titles.

Results appear directly inside the WolfTube library.

---

# ▶️ Playback Resume

WolfTube remembers playback progress for downloaded media.

Playback position can be saved when:

* Pausing media.
* Closing the player.
* Leaving YouTube.
* Switching applications.
* Locking the device.
* Seeking through the timeline.

When the media is opened again, WolfTube can continue from the previously saved position.

After playback finishes completely, the media can start again from the beginning the next time it is played.

---

# 🔒 Lock Screen Controls

Downloaded media integrates with the iOS Lock Screen and Control Center.

WolfTube can display:

* Media artwork.
* Video title.
* Channel name.
* Playback progress.
* Media duration.

For individual media playback, controls can include:

> • Play / Pause
> • Skip Backward
> • Skip Forward
> • Timeline Seeking

When playing media from a playlist, controls can automatically adapt to playlist navigation:

> • Previous Track
> • Play / Pause
> • Next Track

---

# 🔊 Background Playback

WolfTube allows supported videos and audio to continue playing after leaving YouTube.

Background playback can continue while:

* Using another application.
* Returning to the Home Screen.
* Locking the device.
* Playing downloaded videos.
* Playing downloaded audio.
* Listening to WolfTube playlists.

---

# 📺 Picture-in-Picture

Picture-in-Picture allows supported videos to continue playing outside YouTube.

Users can:

* Watch videos while using other applications.
* Resize the floating player.
* Move the PiP window around the screen.
* Return directly to YouTube.

---

# ⚡ Playback Speed

WolfTube expands playback speed controls and provides a wider range of playback speeds.

This can be useful for:

* Tutorials.
* Podcasts.
* Lectures.
* Long videos.
* Music.
* Quickly reviewing content.

---

# 🛠️ Stable Playback

WolfTube includes an optional Stable Playback mode designed to improve playback compatibility and provide a smoother experience in supported environments.

Stable Playback can be enabled or disabled independently.

WolfTube also includes additional playback isolation designed to reduce interference between download-related components and YouTube's native player.

Recent playback compatibility improvements include:

* Better isolation from internal YouTube playback requests.
* Reduced dependency on SABR and Onesie playback components.
* Improved compatibility with regular long-form YouTube videos.
* Diagnostic playback hooks isolated from normal release builds.

---

# 🛡️ SponsorBlock

WolfTube supports SponsorBlock integration for supported videos.

When enabled, WolfTube can automatically skip supported sponsored segments when segment information is available.

SponsorBlock can be independently enabled or disabled from WolfTube settings.

---

# 🚫 Advertisement Reduction

WolfTube includes optional tools for reducing supported advertisements inside YouTube. Because internal ad renderers vary across YouTube/iOS releases, results are not guaranteed.

Features can include:

* Reducing supported advertisements.
* Automatically skipping supported skippable advertisements.
* Providing a cleaner viewing experience.

**Compatibility note:** more aggressive Feed and collection-view ad filtering has caused crashes or missing videos on some iOS 26/27 setups. The v1.36.21-based video-only branch disables invasive Feed filtering and focuses ad-handling on supported in-player requests. The v1.38.2 baseline remains a distinct source snapshot. Some advertisements—including Shorts ads—may remain visible. Ad reduction is best-effort, not guaranteed.

---

# 📱 Shorts Tools

WolfTube integrates directly with YouTube Shorts.

Available tools can include:

* WolfTube action button.
* Video downloading.
* Audio downloading.
* Quick media actions.
* Copy utilities.
* Shorts interface customization.
* Optional floating/draggable WolfTube controls in supported Shorts layouts.

Users can also choose whether WolfTube controls should appear inside Shorts. In the v1.36.21-based UX branch, the Shorts long-press path is separated from the normal player gesture setting, with an additional button visibility option; whether the button appears depends on the installed YouTube build.

---

# 👤 Channel & Profile Tools

WolfTube adds additional utilities directly to supported YouTube channel and profile pages.

### Profile Pictures

* Download channel profile pictures.
* Retrieve the highest available image quality.
* Save or share the image.

### Channel Information

Users can quickly copy:

> • Channel Name
> • Channel ID
> • Channel URL
> • Channel Description

WolfTube tools can be accessed directly without leaving the channel page.

---

# 📋 Video Tools

WolfTube adds useful actions directly to regular YouTube videos.

Available tools include:

* Download video.
* Download audio.
* Download thumbnail.
* Copy video title.
* Copy complete video description.
* Access additional WolfTube media options.

---

# 💬 Comment Tools

WolfTube makes working with YouTube comments easier.

Users can copy individual comments directly without manually selecting the text.

This can be useful for:

* Links.
* Commands.
* Tutorials.
* Long comments.
* Important information.

---

# 📌 Pinned Playlists

Favorite playlists can be pinned so they always remain easily accessible at the top of the WolfTube library.

This is especially useful for users with large media collections.

---

# 📤 Playlist Sharing

WolfTube playlists can be shared with other WolfTube users.

This provides an easier way to move or share organized media collections without manually recreating playlist structures.

---

# 💾 Selective Backup & Restore

WolfTube includes tools for backing up the local media library.

Before exporting, users can select **exactly what their `.wtbackup` archive contains**, rather than automatically sharing the entire library.

Quick presets include:

> • **Settings only** — no media files or personal library history
> • **Videos only** — no unrelated audio or settings
> • **Settings + videos**
> • **Everything except Private**
> • **Everything including Private**, with explicit confirmation

A detailed selection mode also offers settings, videos, audio, playlists, selected library information/history, and a separate **Include Private** option. Private files and private playlist records are excluded by default, and only media files belonging to selected items are copied.

Selective backups can be restored using the included import path, with handling for settings-only archives as well as older backup formats.

**Privacy notice:** `.wtbackup` files are **not encrypted**. Choosing what to include helps limit exposure, but does not make an exported file confidential. Keep backups secure and inspect the selected content before sharing.

---

# 🎨 Native YouTube-Inspired Interface

WolfTube is designed to visually integrate with YouTube.

The interface follows the application's appearance and supports both light and dark environments.

WolfTube avoids unnecessarily separate interface styles and instead aims to make tools feel like part of YouTube itself.

WolfTube also includes additional compatibility handling for YouTube's native Tab Bar.

The native navigation bar is preserved while WolfTube tools are added. Compatibility guards target situations where the original tabs disappear or the Shorts tab bar changes appearance. The floating Liquid Glass treatment is reapplied on supported transitions, while avoiding template tinting of the profile image in the **You** tab. Exact results still depend on YouTube and iOS versions.

The current shared WolfTube branding uses the **white wolf-head logo** rather than the previous red icon.

---

# 🖤 Classic, Studio, Signature & Liquid Glass

WolfTube retains its **white wolf logo**, Dark Premium identity, and signature-style WolfTube wordmark. The Signature header uses a suitable iOS font where available, with a fallback.

Users can choose between **Classic** and **Studio** for WolfTube-owned screens:

* **Classic** — the established WolfTube interface.
* **Studio** — a cleaner graphite presentation with restrained accents, light separators, and more cohesive settings, playlist, and library styling.

**The choice does not redesign YouTube's native interface.** Overlays opened from the video player or Shorts—including the WolfTube action menu, media download sheet, and supported floating controls—retain their glass-like appearance. Older systems can use fallback blur surfaces where necessary; OLED-black appearance remains available in supported areas.

The landscape player can place the **Lock** control in the left-side free area at mid-height while positioning the WolfTube action control alongside supported player tools without overlapping YouTube's native buttons. Player geometry can differ by YouTube release.

---

# 🎛️ Wolf Studio — Personalization & Preview

Open **WolfTube Settings → Wolf Studio** in the v1.36.21-based development branch. The distinct v1.38.2 source baseline names the older experience **Design Studio+**.

| Area | Supported controls in the development branch |
| --- | --- |
| Appearance | Classic / Studio for supported WolfTube screens |
| Download indicator | Glass, circle, compact/mini, card, or hidden where supported; adjustable indicator size |
| Progress geometry | Bar width, bar thickness, ring thickness, supported corner styles |
| Colors | User-defined progress gradients (up to 12 stops), stop ordering, indicator background/text colors |
| Live progress preview | Drag a percentage slider without starting a download; actual `WTDownloadProgressCard` component in the download scene |
| Player | Supported progress appearance and optional recommendation/end-card visibility controls |
| Shorts | Added progress line styling/visibility, tool-button visibility, supported visual options |
| Interface | Supported selected-tab styling, dynamic-glass settings, library/mini-player options |
| Motion | Spring, fade, slide or reduced animation where available and compatible |
| Presets | Save/restore up to eight user-defined style configurations |

**Preview accuracy:** the download-indicator scene uses the actual download component. Player, Shorts and interface scenes are interactive representations driven by real preference values, **not** an embedded running YouTube player. Individual features update when their corresponding runtime integration is supported.

**Preference behavior differs by branch:** the v1.38.2 Design Studio+ documentation describes staged **Apply / Discard / Continue editing** changes. The v1.36.21-based Wolf Studio development work instead describes directly saved customization and saved presets. Do not assume both flows exist in a single installed build.

**Design scope:** customization targets WolfTube-owned components. Original YouTube playback controls and the Feed are not comprehensively reskinned. Existing glass overlays over the player and Shorts remain glass-styled.

---

# 🌙 Dark Mode

WolfTube supports dark mode and uses colors designed to better match YouTube's own dark appearance.

Interface elements automatically adapt to the current appearance where supported.

---

# ⚙️ Organized Settings

WolfTube provides a dedicated settings interface for controlling individual features. In the v1.38.2 Design Studio+ baseline, changes can be previewed before applying. In the v1.36.21-based Wolf Studio development branch, supported customization is saved directly with optional style presets. Behavior depends on the installed build.

Settings are organized into logical categories such as:

### Downloads

> • Video Downloads
> • Audio Downloads
> • Media Library
> • Playlist Features

### Playback

> • Background Playback
> • Picture-in-Picture
> • Stable Playback
> • Playback Speed

### YouTube Experience

> • Advertisement Reduction
> • SponsorBlock
> • Shorts Controls

### WolfTube Buttons

> • Video Button
> • Shorts Button
> • Channel Button
> • Profile Button

### Library & Interface

> • Private Library authentication timeout
> • Customize library sections
> • New playlist artwork behavior
> • Optional mirroring of WolfTube controls when YouTube is in Arabic
> • Liquid Glass / appearance controls

### Interface

> • Language
> • Appearance
> • WolfTube interface options
> • Wolf Studio in the development branch (organized areas, component-linked download preview, custom gradients, progress geometry, presets)
> • Floating download HUD style, position and animation

Users can enable only the WolfTube features they want.

---

# 🐺 YouTube Integration

WolfTube integrates its controls throughout supported areas of YouTube.

WolfTube tools can appear on:

> • Regular videos
> • Shorts
> • Channel pages
> • Profile pages
> • Downloaded media
> • WolfTube playlists

Button visibility can be controlled independently from WolfTube settings.

---

# 🌍 Multi-Language Support

WolfTube supports multiple interface languages, including Arabic and English. The Wolf Studio development branch uses WolfTube's selected language for its supported UI strings and includes a fix for right-to-left slider layout; any untranslated strings or view-alignment regressions should be reported with screenshots.

The interface is designed to correctly handle:

* Left-to-right layouts.
* Right-to-left layouts.
* Icon alignment.
* Text spacing.
* Different interface lengths across languages.
* Playlist playback controls in RTL layouts.
* Arabic labels and icon spacing within the unified download sheet.
* Optional layout mirroring based on the **YouTube app language**, independently from the WolfTube settings language.

---

# 💬 Native-Style Notifications

WolfTube uses cleaner application-style notifications and feedback for supported actions, including a rounded **Liquid Glass-style Undo** banner for supported deletions.

This provides a more consistent visual experience instead of relying on unrelated system-style messages. The v1.36.21-based UX branch additionally routes supported Wolf Studio confirmation dialogs through WolfTube's glass-style dialog UI and can ask whether to close YouTube after settings change. A short exit animation can precede process termination, but iOS does not provide a guaranteed automatic relaunch through this flow.

---

# 🧰 Reliability & Developer Tooling

WolfTube's source includes project validation, compatibility checks, static audits, and optional **developer-only** Frida diagnostic scripts. These are intended for investigating YouTube changes and do not replace real-device testing.

The former **Crash Logs** screen and WolfTube-specific automatic crash/session logger are not part of the current in-app experience. The source keeps compatibility stubs where needed for linking, but these do not write new crash-log files. Updating does **not** automatically delete log files produced by older builds on a device.

Stability safeguards for iOS 27 Feed/collection behavior are separate from the removed logging features.

---

# 🧱 Build Compatibility

Recent WolfTube updates also include improvements for Theos and different iOS SDK environments.

Build-related fixes include:

* Improved compatibility with older iOS SDK headers.
* Removed unsupported direct dependency on `mach/mach_vm.h`.
* Added compatibility handling for `SECT_CSTRING`.
* Fixed the arm64 `_vm_region` linker error.
* Added runtime resolution for supported Mach memory APIs.
* Improved project auditing before releases.

---

# 📱 Compatibility

WolfTube is designed for YouTube on iOS.

Feature availability can vary depending on:

* iOS version.
* Installed YouTube version.
* Installation environment.
* Availability of individual YouTube features.
* Available media formats for each video.

WolfTube is continuously adapted as YouTube and iOS evolve.

---

# 🔧 Verification & Known Limitations

The project includes static audit and source-level regression checks for UI, backups, and selected feature paths. These tests do **not** confirm that the current source compiles with every Theos/iOS SDK or behaves correctly on every iPhone.

In particular, confirm on-device behavior of Studio/Classic switching, the correct save/apply flow for the chosen branch, Wolf Studio live preview and Arabic RTL sliders, custom color stops and dimensions, player/Shorts glass overlays, Shorts button/long press, floating tab bar, 2160p video **and** audio playback, settings-exit confirmation, audio seeking, Private authentication, selective backups, and iOS 26/27 Feed/ad handling before treating them as fully verified. The included source checks cover selected regression risks only.

---

# 📦 Installation

1. Open the latest WolfTube release.
2. Download the WolfTube package from the **Assets** section.
3. Install or sign the application using a supported installation method.
4. Open YouTube.
5. WolfTube features will automatically appear throughout supported parts of the application.

# ❤️ Support WolfTube

If you enjoy WolfTube:

⭐ Star the repository
📢 Share WolfTube
🐛 Report reproducible issues
💡 Suggest useful features

---

# ⚖️ Disclaimer

WolfTube is an independent project and is not affiliated with, endorsed by, or sponsored by YouTube or Google.

YouTube and related trademarks belong to their respective owners.

Users are responsible for complying with applicable platform terms, copyright rules, and local laws when downloading or storing media.

---

<div align="center">

## 🐺 WolfTube

### Your YouTube. Your Media. Your Way.

**Lead developer:** [@inc_inc](https://t.me/inc_inc) · **Assistant developer:** Abd Al-Rahman ([@cc7iq](https://t.me/cc7iq))

**Updates:** [Telegram](https://t.me/inc_ipa) · **Donations:** [Official Binance instructions](https://t.me/inc_ipa/8502)

</div>
