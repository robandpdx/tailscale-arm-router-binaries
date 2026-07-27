# tailscale-arm-router-binaries
Tailscale binaries that have been compressed using upx.

This repo consists of 2 GitHub actions workflows.

## 1. Build and release compressed tailscale ARM64 binaries
- Triggered by workflow dispatch and takes a version as input
- Downloads the specified version of the tailscale for ARM64 from https://pkgs.tailscale.com/stable/#static
- Runs `upx –best` on tailscale and tailscaled
- Creates a new release uploading a zip with the recompressed binaries

## 2. Check upstream tailscale ARM64 version
- Checks https://pkgs.tailscale.com/stable/#static if there’s a new version that doesn’t match an already published release by the first workflow
- If not, triggers the first workflow with the version as input
- Runs on a schedule each Monday at 3:17 AM UTC

