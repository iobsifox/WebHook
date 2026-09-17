# WebHook — Public Binary Releases

> **Source code is PRIVATE** and lives in a separate repository.
> This public repo hosts **signed binaries + checksums only**.

## Layout

```
releases/
  vX.Y.Z/
    WebHook-<ver>-Setup.exe        # Windows Installed (NSIS, signed)
    WebHook-<ver>-portable.exe     # Windows Portable (signed)
    WebHook-<ver>.AppImage         # Linux Portable
    webhook_<ver>_amd64.deb        # Linux Installed
    WebHook-<ver>.dmg / .zip       # macOS (signed + notarized)
    webhook-server-<ver>.tar.gz    # Self-hosted Enterprise bundle
    SHA256SUMS.txt                 # verify every download against this
```

## Verify before installing

```bash
sha256sum -c SHA256SUMS.txt
```

GitHub Releases on this repo mirror each `releases/vX.Y.Z` directory.
Editions: **Personal** (direct P2P, no account) + **Enterprise** (self-hosted server).
Clients: Windows 10 1809+ · macOS 10.15+ · Linux kernel 5.4+.
