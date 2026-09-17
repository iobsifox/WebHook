# WebHook v2.1.0 — release manifest (2026-09-17, ObsiFox Studio)

Personal (direct P2P, no account) + Enterprise (self-hosted server).
Clients: Windows 10 1809+ · macOS 10.15+ · Linux kernel 5.4+.

> Unsigned CI builds (GitHub Actions, one native runner per OS).
> Verify with `SHA256SUMS.txt`. SmartScreen/Gatekeeper warnings are expected
> until code-signing is configured.

| File | Purpose | Install |
|---|---|---|
| `WebHook-2.1.0.exe` | Windows — ONE AnyDesk-style exe | Double-click = portable; in-app Install (per-user, no UAC) or all-users (UAC) |
| `WebHook-2.1.0-win.zip` | Windows unpacked | Extract & run `WebHook.exe` |
| `WebHook-2.1.0.AppImage` | Linux portable | `chmod +x` and run |
| `WebHook-2.1.0.deb` | Linux installed (amd64) | `sudo dpkg -i` |
| `WebHook-2.1.0.dmg` | macOS installer | Open & drag to Applications |
| `WebHook-2.1.0.zip` | macOS app (unsigned zip) | Unzip → right-click Open (first run) |
| `webhook-server-2.1.0.tar.gz` | Enterprise server bundle | See `.env.example` + `docker-compose.yml` inside |

## v2.1.0 highlights

- **New design** (ObsiFox dark-navy design system): frameless custom title bar,
  sidebar, hero + action cards, device cards, side panels, status bar.
- **Fonts**: Ubuntu (EN) · Vazirmatn (FA) · Google Material Icons — bundled,
  fully offline.
- **Full RTL**: فارسی flips the **entire app** right-to-left (numbers/codes stay LTR).
- **Popup notifications**: incoming connection requests pop up as a dedicated
  always-on-top window (name, ID, address, 60s countdown, Accept/Reject) — even
  while the app sits in the tray.
- **No more bare "unknown"**: connection failures show a typed, translated
  reason (bad code · not found · refused · timeout · rejected · relay down…).
- **Internet mode — Assist Relay (Mode 4)**: two devices on **completely
  different internets** (different ISPs / CGNAT / mobile) finally connect.
  Run ONE tiny zero-knowledge relay (RAM-only, blind forwarding, no decrypt
  path), e.g.: `docker compose --profile assist up -d assist` (port 8090) or
  `node dist/index.js` from the `assist-point` folder. Then on BOTH devices:
  **Settings → «حالت اینترنتی — رله امدادی»** → `ws://<host>:8090` (or
  `wss://…` behind TLS) → **Test relay** → **Save**. Dial the partner's 9-digit
  ID as usual. Relayed sessions show a `relay` badge next to the safety number;
  end-to-end encryption (X25519 3-DH → ChaCha20-Poly1305) is identical to LAN.

226 automated tests green on Windows/macOS/Linux; all Actions pipelines green.

Unattended mode: `WEBHOOK_AUTO_ACCEPT=1` or `--auto-accept`.
Enterprise deploy: `tar -xzf webhook-server-2.1.0.tar.gz && cp .env.example .env` (edit) `&& docker compose up -d --build`.
