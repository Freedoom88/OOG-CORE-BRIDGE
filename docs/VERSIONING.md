# Versioning

OOG Core Bridge uses Semantic Versioning for machine-readable versions.

## Product launcher

- Executable name: `OOGCoreBridge.exe`
- First public release: `1.0.0`
- User-facing version may be displayed as `v1.0.0`.

## Core runtime

- Runtime executable name: `OOGCoreRuntime.exe`
- First public release: `1.0.0`
- Core version is primarily internal and may advance independently from the launcher.

Examples:

- `1.0.1` — patch/fix
- `1.1.0` — feature release
- `2.0.0` — major release

Version parts are numeric, so `1.0.10` is newer than `1.0.9`.

## Release tags

Use component-specific tags so launcher and Core can be updated independently:

- `core-v1.0.0`
- `launcher-v1.0.0`

Do not put version numbers in installed executable filenames. The updater always targets stable paths.
