# WolfTube Release Channels — permanent contract

The update service is the existing Railway production service. Do not create a second API or Telegram bot.

- Repository: `inc1x/WolfTube`
- Railway API: `https://wolftube-control-api-production.up.railway.app`
- Update endpoint: `/api/v1/wolftube/update`
- GitHub sync endpoint: `POST /api/v1/github/release-sync`
- Legacy endpoint: `/api/wolftube/update` (Stable-only compatibility)

## Build identity

Every IPA must be built with:
- `Version`: from the Theos `control` file
- `Build`: `WOLFTUBE_BUILD_NUMBER` or the generated numeric form of Version
- `Channel`: one of `stable`, `beta`, `alpha`, `experimental`

The Theos build hook generates `WolfTubeUpdateBuildConfig.h` before compilation. Examples:

```sh
make package
WOLFTUBE_RELEASE_CHANNEL=beta make package
WOLFTUBE_RELEASE_CHANNEL=alpha make package
WOLFTUBE_RELEASE_CHANNEL=experimental make package
WOLFTUBE_RELEASE_CHANNEL=beta WOLFTUBE_BUILD_NUMBER=13623 make package
```

## Release manifest

Attach a `wolftube-release.json` asset beside the IPA. Use the generator:

```sh
python3 Tools/generate_release_manifest.py --notes release-notes.md --output wolftube-release.json
```

Example:

```json
{
  "app": "WolfTube",
  "version": "1.36.22",
  "build": 13622,
  "channel": "stable",
  "release_notes": "Release notes..."
}
```

The API can also read `WolfTube-Version`, `WolfTube-Build`, and `WolfTube-Channel` fields from the GitHub release body. Old releases without a manifest may be inferred from the DEB package version or release name/tag. Do not use filename-only guesses for new releases.

## GitHub → Railway automation

The workflow `.github/workflows/wolftube-release-sync.yml` runs for `release.published` and `release.prereleased`. It calls Railway only after a release event. The API independently verifies that the tag exists and has a public uploaded IPA asset with non-zero size and an HTTPS download URL.

Configure one GitHub repository Actions secret:

- Name: `WOLFTUBE_RAILWAY_SYNC_SECRET`
- Value: the same value as Railway's `GITHUB_SYNC_SECRET`

Never put that value in the IPA, source files, release manifest, README, or public Actions variables. Telegram tokens and webhook secrets remain Railway-only.

## Channel isolation

- Stable users receive Stable policy only.
- Beta/Alpha/Experimental users receive only their embedded app channel policy.
- A release in one channel must never overwrite another channel's latest Version, Build, IPA, notes, minimum supported build, or force-update setting.
- Publishing a release never enables force update.
- The old API route remains Stable-only.

## Release-ready gate

A release is not update-ready unless it is published, non-draft, contains a successfully uploaded IPA, has non-zero asset size, and has a valid HTTPS download URL. A DEB, source ZIP, or GitHub source archive is not an IPA.

## Future release checklist

1. Update `control: Version` and choose the intended build channel.
2. Run Theos build; inspect generated `WolfTubeUpdateBuildConfig.h`.
3. Install and test the IPA on a real iPhone.
4. Generate and attach `wolftube-release.json`.
5. Publish GitHub Release with the correct channel.
6. Confirm the GitHub Actions sync workflow succeeds.
7. Confirm the intended Railway channel updates and the other three remain unchanged.
8. Confirm Telegram dashboard metadata and optional announcement.
9. Never enable force update without an explicit admin decision and a valid IPA.
