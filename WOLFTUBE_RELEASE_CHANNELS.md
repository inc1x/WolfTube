# WolfTube Release Channels — Permanent Contract

This repository's release automation is part of the WolfTube application architecture.
Do not remove it when creating Stable, Beta, Alpha, Experimental, hotfix, or branch builds.

## Canonical update service

- Base URL: https://wolftube-control-api-production.up.railway.app
- Legacy Stable endpoint (backward compatibility): /api/wolftube/update
- Versioned endpoint: /api/v1/wolftube/update?version=<VERSION>&build=<BUILD>&channel=<CHANNEL>
- GitHub release sync endpoint: POST /api/v1/github/release-sync
- Repository: inc1x/WolfTube

## Release channels

Allowed channel values are exactly:
- stable
- beta
- alpha
- experimental

Every IPA release must declare its channel explicitly. The recommended source of truth is a GitHub Release asset named `wolftube-release.json`:

```json
{
  "app": "WolfTube",
  "version": "1.40.11",
  "build": 14011,
  "channel": "beta",
  "release_notes": "Short release notes"
}
```

The release body may also include:
- `WolfTube-Version: 1.40.11`
- `WolfTube-Build: 14011`
- `WolfTube-Channel: beta`

If both manifest and body metadata are provided, the manifest takes precedence.
Do not infer a channel solely from GitHub's prerelease boolean when explicit metadata exists.
GitHub's prerelease flag is a fallback signal for Beta, not a replacement for explicit channel metadata.

## Build metadata in the iOS source

Every build must embed:
- WT_UPDATE_BASE_URL = https://wolftube-control-api-production.up.railway.app
- WT_UPDATE_API_PATH = /api/v1/wolftube/update
- WT_APP_VERSION = actual CFBundleShortVersionString / package version
- WT_BUILD_NUMBER = actual monotonically increasing CFBundleVersion / package build
- WT_RELEASE_CHANNEL = stable | beta | alpha | experimental

No BOT_TOKEN, DATABASE_URL, GITHUB_SYNC_SECRET, Telegram webhook secret, or other server secret may be embedded in the IPA.

The installed app must query the endpoint with version, build, and channel. It must fail open for connectivity errors: a failed request is not a forced update. Force-update state is only an explicit channel policy set by an administrator.

## GitHub publication rules

- GitHub Releases are the source of truth for published artifacts.
- A release is not update-ready unless it is published, has an uploaded non-empty IPA asset, and the HTTPS asset URL is valid.
- Releases without IPA are skipped and never replace the current channel's working IPA.
- Beta/Alpha/Experimental do not change Stable.
- Each channel has independent latest version/build, IPA URL, release notes, minimum supported version/build, force-update flag, and publication date.
- The release workflow calls the Railway sync endpoint after publication.
- The GitHub Actions repository secret `WOLFTUBE_SYNC_SECRET` must equal Railway's `GITHUB_SYNC_SECRET`.

## Telegram controls

The Telegram admin dashboard selects one channel at a time. Manual release metadata, minimum supported version, force-update, update message, release notes, and announcements apply only to that selected channel.
Subscribers opt into notification channels independently. The application channel and Telegram notification preferences are separate concepts.

## Compatibility

- Keep /api/wolftube/update available for older Stable clients.
- New clients use /api/v1/wolftube/update.
- Never force-update a client because Railway/GitHub is unreachable.
- A client without the updater cannot be remotely forced to upgrade.
- A channel with no valid IPA has no downloadable update and cannot force-update.

## Required release checks

1. Verify Version and Build are both present and match the compiled IPA metadata.
2. Verify the release channel manifest.
3. Upload the IPA before publishing the GitHub Release.
4. Verify the asset is uploaded and non-empty.
5. Publish the release.
6. Wait for WolfTube Release Sync workflow to succeed.
7. Verify the matching channel API response.
8. Verify other channels' latest release did not change.
9. Only then announce the release; force update remains disabled unless explicitly enabled by an administrator.

## Build-source prerequisite

The current public GitHub repository must contain the complete Theos source and build workflow before GitHub Actions can build IPAs from source. A release-sync workflow only synchronizes published IPA assets; it does not compile missing source code.
