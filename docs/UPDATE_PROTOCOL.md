# OOG Core Bridge update protocol

The public GitHub repository is only the binary delivery channel. Supabase remains the authority for version policy and SHA-256.

## User-facing files

- `OOGCoreBridge.exe` — launcher, license client and updater.
- `OOGCoreRuntime.exe` — internal Core binary. The launcher keeps it hidden in normal Explorer view.

Version numbers are not part of either filename.

## Core update flow

1. Launcher validates the saved/entered license through Supabase.
2. `launch` returns an Ed25519-signed launch payload.
3. The signed payload contains Core update metadata from `update_manifest`:
   - `core_update_latest_version`
   - `core_update_minimum_version`
   - `core_update_download_url`
   - `core_update_sha256`
   - `core_update_force_update`
   - `core_update_revision`
4. Launcher verifies the Ed25519 signature before trusting the URL/hash.
5. If an update is needed, Launcher downloads only from the official GitHub Release path.
6. Download goes to `OOGCoreRuntime.exe.new`.
7. SHA-256 must match the signed manifest before installation.
8. The old Core is temporarily renamed to `.bak`, the verified `.new` file is moved into place, and the version marker is written.
9. Launcher requests a fresh launch ticket for the newly installed Core version, then starts Core through the inherited ticket pipe.

If download, hash verification, or replacement fails, the previous Core remains/restores in place.

## Release versions

Development versions remain `0.x` until the first production release. The first production baseline will reset both components to:

- Launcher: `1.0.0`
- Core: `1.0.0`

Future updater comparisons use numeric `MAJOR.MINOR.PATCH` components, so for example `1.0.10 > 1.0.9`.
