# Release pipeline

This repository is a public binary distribution channel. Source code and secrets must remain outside this repository.

## Components

### Launcher

Installed filename:

`OOGCoreBridge.exe`

First public version:

`1.0.0`

### Core runtime

Installed filename:

`runtime/OOGCoreRuntime.exe`

First public version:

`1.0.0`

The Core runtime may be updated independently from the launcher.

## Core update flow

1. Launcher validates the license through the backend.
2. Launcher requests update metadata from the backend.
3. Backend returns the current Core version, minimum version, download URL, SHA-256 and update policy.
4. Launcher compares semantic versions numerically.
5. If an update is required, Launcher downloads the package to a temporary file.
6. Launcher verifies SHA-256 before touching the installed runtime.
7. The previous runtime is preserved as a rollback copy while the new package is installed.
8. Only after successful verification and install does Launcher request/continue the launch-ticket flow and start the Core runtime.

## Distribution source of truth

- Supabase/backend: authoritative version/update policy and SHA-256 metadata.
- GitHub Releases: binary storage/distribution only.
- The Git repository itself must not contain application binaries or source code.

## Release asset convention

Core release tag:

`core-vMAJOR.MINOR.PATCH`

Recommended Core package asset:

`OOGCoreRuntime-win64.zip`

Launcher release tag:

`launcher-vMAJOR.MINOR.PATCH`

Recommended Launcher asset:

`OOGCoreBridge-win64.zip`

The release tag carries the version. Installed filenames stay constant.

## Production order

For each production build:

1. Build from the clean source baseline.
2. Run release-mode validation/tests.
3. Apply approved protection/obfuscation.
4. Code-sign production binaries when signing is enabled.
5. Build the final distribution package.
6. Calculate SHA-256 from that exact final package.
7. Upload the package to the matching GitHub Release.
8. Update backend manifest only after the final GitHub asset and SHA-256 are known.

Never calculate the production SHA-256 before the final protection/signing/package step, because any later byte change invalidates the hash.
