# WebHook v2.0.2 — release manifest (2026-09-17, ObsiFox Studio)

Personal (direct P2P, no account) + Enterprise (self-hosted server).
Clients: Windows 10 1809+ · macOS 10.15+ · Linux kernel 5.4+.

> These `v2.0.2` binaries are **unsigned local builds** (cross-built on Linux).
> Verify with `SHA256SUMS.txt`. Signed + notarized builds are produced by CI
> (`release.yml`) on native runners once code-signing secrets are configured
> (see `SIGNING.md` in the private source repo).

| File | Purpose | Install |
|---|---|---|
| `WebHook-2.0.2.exe` | Windows — ONE AnyDesk-style exe | Double-click = portable; in-app Install (per-user, no UAC) or all-users (UAC) |
| `WebHook-2.0.2.AppImage` | Linux Portable | `chmod +x` and run |
| `WebHook-2.0.2.deb` | Linux Installed (amd64) | `sudo dpkg -i` |
| `WebHook-2.0.2.zip` | macOS app (unsigned zip) | Unzip → right-click Open (first run) |
| `webhook-server-2.0.2.tar.gz` | Enterprise server bundle | See `.env.example` + `docker-compose.yml` inside |

v2.0.2 highlights: fixed the `__dirname is not defined` startup crash
(ESM-safe `mainDirname` shim) — the window now opens; 198 tests (U/I/F/E2E/R)
all green, including a no-bare-`__dirname` regression scanner.

Windows SmartScreen / macOS Gatekeeper will warn on unsigned builds — expected
until the OV/EV certificate release (CI already wired, needs secrets only).
Enterprise deploy: `tar -xzf webhook-server-2.0.2.tar.gz && cp .env.example .env` (edit secrets) `&& docker compose up -d --build`.
