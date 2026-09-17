# WebHook v2.0.5 — release manifest (2026-09-17, ObsiFox Studio)

Personal (direct P2P, no account) + Enterprise (self-hosted server).
Clients: Windows 10 1809+ · macOS 10.15+ · Linux kernel 5.4+.

> These v2.0.5 binaries are **unsigned CI builds** (GitHub Actions, one native
> runner per OS — the first pipeline-produced release). Verify with
> `SHA256SUMS.txt`. Signed + notarized builds follow once the code-signing
> secrets are configured (release.yml now skips signing gracefully when unset).

| File | Purpose | Install |
|---|---|---|
| `WebHook-2.0.5.exe` | Windows — ONE AnyDesk-style exe | Double-click = portable; in-app Install (per-user, no UAC) or all-users (UAC) |
| `WebHook-2.0.5-win.zip` | Windows unpacked | Extract & run `WebHook.exe` — use if the single exe is blocked |
| `WebHook-2.0.5.AppImage` | Linux Portable | `chmod +x` and run |
| `WebHook-2.0.5.deb` | Linux Installed (amd64) | `sudo dpkg -i` |
| `WebHook-2.0.5.zip` | macOS app (unsigned zip) | Unzip → right-click Open (first run) |
| `WebHook-2.0.5.dmg` | macOS installer image (new) | Open & drag to Applications |
| `webhook-server-2.0.5.tar.gz` | Enterprise server bundle | See `.env.example` + `docker-compose.yml` inside |

v2.0.5 highlights — **the missing wire**: since the first 2.0.x builds the
client never opened a socket, so a connection request could never reach the
person running the app in the background — not even between two PCs behind one
modem. v2.0.5 adds the Session Link: the app listens from boot (TCP 47821 +
LAN discovery UDP 47820), the partner's screen shows a real **Accept/Reject
prompt**, and the session is end-to-end encrypted (X25519 3-DH →
ChaCha20-Poly1305) with a comparable **safety number** on both sides. Dial by
9-digit ID (same LAN), `WH1.…` code, or `host:port`. Devices tab lists LAN
peers; encrypted chat proves the pipe. 219 tests (U/I/F/E2E/R) all green on
Windows/macOS/Linux.

Unattended mode: `WEBHOOK_AUTO_ACCEPT=1` or `--auto-accept`.
Windows SmartScreen / macOS Gatekeeper will warn on unsigned builds — expected
until certificates are configured. Enterprise deploy:
`tar -xzf webhook-server-2.0.5.tar.gz && cp .env.example .env` (edit) `&& docker compose up -d --build`.
