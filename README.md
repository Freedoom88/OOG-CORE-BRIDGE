# OOG Core Bridge

Official public distribution channel for OOG Core Bridge runtime releases.

This repository is intentionally used for distribution only. Application source code, license secrets, signing seeds, Supabase service keys, and other private credentials must never be committed here.

## Distribution model

- `OOGCoreBridge.exe` — user-facing launcher/updater executable.
- `OOGCoreRuntime.exe` — internal Core runtime delivered by the updater.
- Release binaries are verified by SHA-256 before installation.
- Version/update policy is controlled by the OOG licensing backend.

Do not download or run binaries from unofficial mirrors.
