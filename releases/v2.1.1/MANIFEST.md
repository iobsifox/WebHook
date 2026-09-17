# WebHook v2.1.1 — Release Manifest / مانیفست انتشار

**Release date / تاریخ انتشار:** 2026-09-17
**Source ref / مرجع سورس:** `iobsifox/webhook` @ tag `v2.1.1` (main = `56713fd`)
Built by GitHub Actions from the private source repo; published manually.

## What's fixed / چی درست شد

- **`Connection failed — Unknown cipher` رفع شد.** Runtimeٔ الکترون (BoringSSL)
  رمز `chacha20-poly1305` را ندارد؛ در 2.1.0 هر سشن روی اولین فریم رمزنگاری‌شده
  می‌مرد. حالا کلاینت در connect-request فهرست رمزها را می‌فرستد و میزبان
  اولین رمز مشترک را برمی‌گزیند: **AES-256-GCM به‌عنوان fallbackِ همگانی**.
- Incompatible peers now get a clear, translated `no common cipher` error
  instead of a crash; the negotiated cipher is shown next to the session
  safety number (`· aes-256-gcm`).

> ⚠️ **هر دو دستگاه را به 2.1.1 ارتقا دهید / Upgrade BOTH devices to 2.1.1.**
> Two 2.1.1 installs always negotiate a working cipher; 2.1.0↔2.1.1 pairs only
> work when at least one side offers AES. دو نصب 2.1.1 همیشه به رمز مشترک می‌رسند.

## Files / فایل‌ها

| File | Platform |
|---|---|
| `WebHook-2.1.1.exe` | Windows installer (NSIS) |
| `WebHook-2.1.1-win.zip` | Windows portable |
| `WebHook-2.1.1.AppImage` | Linux |
| `WebHook-2.1.1.deb` | Debian/Ubuntu |
| `WebHook-2.1.1.dmg` | macOS |
| `WebHook-2.1.1.zip` | macOS (zip) |
| `webhook-server-2.1.1.tar.gz` | Enterprise server bundle |
| `SHA256SUMS.txt` | checksums for all of the above |

Verify: `sha256sum -c SHA256SUMS.txt`
بررسی صحت: دستور بالا را در کنار فایل‌ها اجرا کنید.

## Security notes / نکات امنیتی

- **Unsigned CI builds.** Windows SmartScreen and macOS Gatekeeper will warn
  («Unknown publisher» / «unidentified developer»). This is expected; verify
  the SHA-256 checksum above. Builts are not code-signed yet.
  بیلدها امضای کد ندارند؛ هشدار SmartScreen/Gatekeeper طبیعی است — چک‌سام را چک کنید.
- To run the DMG on macOS: right-click → Open, or
  `xattr -dr com.apple.quarantine WebHook-2.1.1.dmg`.
- End-to-end encryption of sessions is unchanged (X25519 + HKDF + AEAD); only
  the AEAD algorithm is now **negotiated** with AES-256-GCM fallback.
