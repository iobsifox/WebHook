# WebHook v2.0.1 — release manifest (2026-09-17, ObsiFox Studio)

Personal (direct P2P, no account) + Enterprise (self-hosted server).
Clients: Windows 10 1809+ · macOS 10.15+ · Linux kernel 5.4+.

> These `v2.0.1` binaries are **unsigned local builds** (cross-built on Linux).
> Verify with `SHA256SUMS.txt`. Signed + notarized builds are produced by CI
> (`release.yml`) on native runners once code-signing secrets are configured
> (see `SIGNING.md` in the private source repo).

| File | Purpose | Install |
|---|---|---|
| `WebHook-2.0.1.exe` | Windows — ONE AnyDesk-style exe | Double-click = portable; in-app Install (per-user, no UAC) or all-users (UAC) |
| `WebHook-2.0.1.AppImage` | Linux Portable | `chmod +x` and run |
| `WebHook-2.0.1.deb` | Linux Installed (amd64) | `sudo dpkg -i` |
| `WebHook-2.0.1.zip` | macOS app (unsigned zip) | Unzip → right-click Open (first run) |
| `webhook-server-2.0.1.tar.gz` | Enterprise server bundle | See `.env.example` + `docker-compose.yml` inside |

v2.0.1 highlights: window-open failure fixed (failsafe visible window,
optional tray, single-instance, `startup.log` diagnostics); full WebHook /
ObsiFox Studio branding with hook-W logo; Windows NSIS setup replaced by the
single exe + in-app Install/Uninstall; 193 tests (U/I/F/E2E/R) all green.

Windows SmartScreen / macOS Gatekeeper will warn on unsigned builds — expected
until the OV/EV certificate release (CI already wired, needs secrets only).
Enterprise deploy: `tar -xzf webhook-server-2.0.1.tar.gz && cp .env.example .env` (edit secrets) `&& docker compose up -d --build`.
