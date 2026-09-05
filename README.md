# OOG Core Bridge

Official public distribution channel for OOG Core Bridge runtime releases.

This repository is intentionally used for distribution only. Application source code, license secrets, signing seeds, Supabase service keys, and other private credentials must never be committed here.

## Distribution model

- `OOGCoreBridge.exe` — user-facing launcher, license client and updater.
- `runtime/OOGCoreRuntime.exe` — internal Core runtime managed by the launcher.
- Installed executable filenames stay constant and do not contain version numbers.
- First public Launcher version: `1.0.0`.
- First public Core version: `1.0.0`.
- Release binaries are published through GitHub Releases, not stored in the Git tree.
- Every downloaded package is verified by SHA-256 before installation.
- Version/update policy is controlled by the OOG backend; GitHub is the binary distribution layer.

## Release tags

- Core: `core-v1.0.0`, `core-v1.0.1`, ...
- Launcher: `launcher-v1.0.0`, `launcher-v1.0.1`, ...

See [`docs/RELEASE_PIPELINE.md`](docs/RELEASE_PIPELINE.md) and [`docs/VERSIONING.md`](docs/VERSIONING.md) for the release rules.

Do not download or run binaries from unofficial mirrors.
