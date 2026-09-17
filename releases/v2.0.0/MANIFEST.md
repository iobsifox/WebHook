# WebHook v2.0.0 — release manifest (2026-09-17)

Personal (direct P2P, no account) + Enterprise (self-hosted server).
Clients: Windows 10 1809+ · macOS 10.15+ · Linux kernel 5.4+.

> These `v2.0.0` binaries are **unsigned local builds** (cross-built on Linux).
> Verify with `SHA256SUMS.txt`. Signed + notarized builds are produced by CI
> (`release.yml`) on native runners once code-signing secrets are configured.

| File | Purpose | Install |
|---|---|---|
| `WebHook-2.0.0.exe` | Windows Installed (NSIS) | Run setup → permanent ID, autostart |
| `WebHook-2.0.0-portable.exe` | Windows Portable | Run from anywhere/USB, zero trace |
| `WebHook-2.0.0.AppImage` | Linux Portable | `chmod +x` and run |
| `WebHook-2.0.0.deb` | Linux Installed (amd64) | `sudo dpkg -i` |
| `WebHook-2.0.0.zip` | macOS app (unsigned zip) | Unzip → right-click Open (first run) |
| `webhook-server-2.0.0.tar.gz` | Enterprise server bundle | See `.env.example` + `docker-compose.yml` inside |

Windows SmartScreen / macOS Gatekeeper will warn on unsigned builds — expected.
Enterprise deploy: `tar -xzf webhook-server-2.0.0.tar.gz && cp .env.example .env` (edit secrets) `&& docker compose up -d --build`.
