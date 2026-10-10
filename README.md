<div align="center">

<img
src="https://github.com/user-attachments/assets/634dfa30-51da-4a3f-a93f-b973c10764f9"
width="155"
alt="WolfTube Logo"
/>

# WolfTube

### A Powerful YouTube Experience for iOS

**Downloads · Private Library · Playlists · Selective Backups · Background Playback · PiP · SponsorBlock · Shorts**

**Latest source update: v1.36.21 — Dark Premium Signature & Landscape Controls**

<br>

> 📦 Download the latest WolfTube package from the **Assets** section of [Releases](https://github.com/inc1x/WolfTube/releases).
>
> ℹ️ Availability and compatibility of individual features depend on the YouTube/iOS version. Some recent interface and ad-filtering changes still require on-device verification.

</div>

---

# ✨ About WolfTube

WolfTube is an advanced enhancement for YouTube on iOS that adds powerful media, playback, library, customization, and productivity features directly inside the YouTube application.

It is designed to feel integrated with YouTube rather than operating as a separate application.

WolfTube allows users to download media, maintain a personal offline library with optional Private access, create playlists with custom artwork, control playback, export only selected content, manage multiple media items, and customize YouTube-integrated tools. Its current interface combines native Liquid Glass surfaces with a Dark Premium settings header and signature-style WolfTube wordmark.

---

# 🆕 What's New — v1.36.21

WolfTube's recent updates focus on customization, privacy, and closer integration with YouTube.

* **Dark Premium settings header:** graphite layers, subtle metallic lighting, the new white wolf insignia, and a signature-style **WolfTube** title (`SnellRoundhand-Bold` where available, with fallback).
* **Landscape player lock:** the lock control targets the center of the left-side empty margin, away from YouTube's native controls. Portrait placement is unchanged. Actual positioning depends on the player layout.
* **New white wolf logo:** a shared icon source for the WolfTube tab, player tool, and settings; no intentional substitution for the user's YouTube profile photo.
* **Persistent floating Tab Bar styling:** reapplication of Liquid Glass after navigation between Home, Shorts, You, and other tabs, with native profile images kept in their original rendering mode.
* **Download-sheet RTL improvements:** independent icon and text layout, better support for long Arabic labels, and subtle burgundy-tinted selection for Video/Audio and save destinations.
* **Classic settings restored:** tap an option to open its choices directly. The experimental Live Preview screen and Experience Studio are not part of the current interface.
* **Playlist creation artwork:** choose whether to be asked for artwork each time, open Photos automatically, or keep the default cover.
* **Selective library export:** control exactly which settings and media are included in a backup; Private items are excluded unless explicitly selected.

The source has undergone static audits; this does **not** guarantee successful compilation or runtime behavior for every version of iOS/YouTube.

---

# 📥 Video & Audio Downloads

WolfTube adds a complete media downloading system directly into YouTube.

### Video Downloads

* Download videos directly from YouTube.
* Choose between multiple available video qualities.
* Support for high-resolution downloads when available.
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

The floating download progress indicator supports different styles and positions, a red progress accent, dragging to reposition, and an available cancel control. Its subtle motion respects iOS **Reduce Motion** where implemented. The settings use classic choice menus, not Live Preview.

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

**Version note:** the legacy renderer-filtering path used before v1.35.3 was reintroduced experimentally for iOS 26/27 in v1.36.19. On iOS 18–25, conservative behavior remains to reduce known collection-layout crash risks. Some ads, including Shorts ads, may still appear; compatibility and stability need real-device validation.

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

Users can also choose whether WolfTube controls should appear inside Shorts.

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

The native navigation bar is preserved while WolfTube tools are added, and recovery protections help prevent situations where the original YouTube tabs disappear and only the WolfTube button remains visible. Recent builds attempt to reapply a floating Liquid Glass tab style after YouTube reconstructs its tabs, while avoiding template tinting of the actual profile picture in the **You** tab.

The current shared WolfTube branding uses the **white wolf-head logo** rather than the previous red icon.

---

# 🖤 Dark Premium, Signature & Liquid Glass

The settings header has a **Dark Premium** visual treatment with a graphite palette, subtle metallic highlights, a glass-like wolf logo tile, and a signature-style WolfTube wordmark. It uses an iOS-provided signature font where supported, with a fallback for compatibility.

WolfTube's supported sheets and library controls use rounded glass-style components. OLED black appearance remains available where implemented, and lighter blur/fallback surfaces are used on older systems.

The landscape player can place the **Lock** control in the left-side free area at mid-height while positioning the WolfTube action control alongside supported player tools without overlapping YouTube's native buttons. Player geometry can differ by YouTube release.

---

# 🌙 Dark Mode

WolfTube supports dark mode and uses colors designed to better match YouTube's own dark appearance.

Interface elements automatically adapt to the current appearance where supported.

---

# ⚙️ Organized Settings

WolfTube provides a dedicated settings interface for controlling individual features.

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
> • Floating download HUD style, position and animation (classic choice menus)

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

WolfTube supports multiple interface languages, including Arabic and English.

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

This provides a more consistent visual experience instead of relying on unrelated system-style messages.

---

# 🧰 Reliability & Diagnostics

WolfTube includes internal tools designed to make development and troubleshooting more reliable.

These include:

* Project validation.
* Compatibility checks.
* Diagnostic tools.
* Static project auditing.
* Playback compatibility isolation.
* Improved issue detection.
* Faster troubleshooting when YouTube changes internal behavior.

The bundled diagnostic scripts and static audits are development aids. They do not replace testing with the actual installed YouTube build.

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

In particular, confirm on-device behavior of the floating tab bar, the signature header, landscape lock placement, Private authentication, selective backups, and iOS 26/27 ad filtering before treating them as fully verified.

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
