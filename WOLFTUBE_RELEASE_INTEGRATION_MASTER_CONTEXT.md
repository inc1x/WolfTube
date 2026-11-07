# WolfTube Release Integration — Permanent Master Rules

Effective 2026-11-07. This file supplements, and does not replace, `WolfTube_PROJECT_MASTER_CONTEXT_V38_1.md`.

## Permanent infrastructure

- GitHub source of truth: `inc1x/WolfTube` Releases.
- Existing Railway project: `WolfTube-Control`.
- Existing Railway service: `WolfTube-Control-API`.
- Environment: `production`.
- Existing PostgreSQL service and existing Telegram bot must be reused.
- Public API base: `https://wolftube-control-api-production.up.railway.app`.
- App update route: `/api/v1/wolftube/update`.
- Legacy route: `/api/wolftube/update` remains Stable-only for older installed builds.
- GitHub webhook route: `POST /api/v1/github/release-sync`.

Do not create duplicate Railway projects, databases, APIs, or bots unless the user explicitly requests it.

## Permanent release identity

Every future WolfTube build, including Stable, Beta, Alpha, Experimental, and any branch/variant, must carry:
- package Version from `control`
- monotonically increasing numeric Build Number
- release channel string
- same public Railway update endpoint

The Theos build hook generates `WolfTubeUpdateBuildConfig.h`. Use:
- `WOLFTUBE_RELEASE_CHANNEL=stable|beta|alpha|experimental`
- `WOLFTUBE_BUILD_NUMBER=<positive integer>` when explicitly overriding the derived number

Do not hardcode channel/version/build in the update gate. Never ship Telegram BOT_TOKEN, TELEGRAM_WEBHOOK_SECRET, or GITHUB_SYNC_SECRET in the IPA or public repository.

## GitHub release metadata

Attach `wolftube-release.json` next to every IPA with:
`app`, `version`, `build`, `channel`, `release_notes`.

The Railway service accepts explicit manifest metadata or the release-body fields:
- `WolfTube-Version: 1.36.22`
- `WolfTube-Build: 13622`
- `WolfTube-Channel: stable|beta|alpha|experimental`

Published releases without a valid uploaded IPA are not update-ready. Never update a channel's policy from a draft, missing IPA, zero-size asset, or invalid/non-HTTPS download URL. Old releases can be inferred from existing DEB package metadata or tag/name where possible, but future releases must have a manifest.

## Channel isolation

The four channels are separate database policies. User app channel is embedded in its build. Telegram subscribers may independently choose which release announcements to receive. Admins select one channel in the dashboard before editing its message, minimum version/build, force-update policy, or announcing it.

Publishing/syncing a release never enables forced update. Force Update is an explicit per-channel admin decision. A Stable release must not update Beta/Alpha/Experimental policies and vice versa.

## Runtime behavior

- Check on app launch, foreground return, and periodically while active.
- Optional update: show dismissible prompt with version/build/notes and IPA link.
- Forced update: only if server explicitly returns a valid force policy and an HTTPS IPA link.
- Network/API failure must not invent a new forced update. Keep only a previously received valid mandatory policy cached.
- Old IPA builds without Update Gate cannot be remotely forced to update retroactively.

## Release automation

GitHub Actions workflow: `.github/workflows/wolftube-release-sync.yml`.
It runs on published/pre-released GitHub Releases and calls Railway. Configure repository Actions secret:
- `WOLFTUBE_RAILWAY_SYNC_SECRET`

Its value must exactly match Railway variable:
- `GITHUB_SYNC_SECRET`

Do not store this secret in source, README, IPA, manifest, or public Actions variables.

## Mandatory pre-release checks

1. Set `control: Version`.
2. Choose the intended channel and build number.
3. Build Theos; inspect generated `WolfTubeUpdateBuildConfig.h`.
4. Install and verify the IPA on iPhone.
5. Generate and attach `wolftube-release.json`.
6. Publish the GitHub Release.
7. Verify GitHub Actions sync succeeded.
8. Verify the intended Railway channel updated.
9. Verify other three channels were unchanged.
10. Verify the Telegram dashboard sees correct metadata.
11. Do not enable force update unless explicitly requested and valid IPA is available.

Preserve this document in every future Master Context. Never claim device testing, full automatic IPA compilation, or end-to-end publication unless each was actually performed.
