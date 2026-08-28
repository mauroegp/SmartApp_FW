# SmartApp_FW — ESP-Firmware Releases

Öffentliches **Release-only**-Repository für vorkompilierte SmartApp-ESP-Firmware.

- **Quellcode & PlatformIO-Projekte:** [mauroegp/SmartApp](https://github.com/mauroegp/SmartApp) (`firmware/`)
- **Dieses Repo:** nur `.bin`-Dateien und Manifeste — keine Firmware-Quellen

## Releases

| Tag | Inhalt |
|-----|--------|
| `firmware-v1.0.0` | Erstes Multi-Modul-Release (7 Binaries + `firmware-manifest.json`) |

Neue Releases werden mit Tag `firmware-v<semver>` veröffentlicht (z. B. `firmware-v1.0.1`).

### Modultypen (v1.0.0)

| Modultyp | Datei | Hardware |
|----------|-------|----------|
| `relay-4` | `relay-4.bin` | ESP32-C3 Super Mini |
| `relay-8` | `relay-8.bin` | ESP32 Dev Module |
| `relay-16` | `relay-16.bin` | ESP32-C3 + 74HC595 |
| `io-4x4` | `io-4x4.bin` | ESP32-C3 Super Mini |
| `io-8x8` | `io-8x8.bin` | ESP32 Dev Module |
| `mppt-bridge` | `mppt-bridge.bin` | ESP32 Dev Module |
| `mppt-io` | `mppt-io.bin` | ESP32 Dev Module |

Weitere Typen (`sensor-esp01`, `homekit-bridge`) folgen in späteren Releases.

## Manifest

Jedes Release enthält **`firmware-manifest.json`** mit Version, SHA256 und Dateinamen pro Modultyp.

Die SmartApp-Cloud/der Server lädt Updates über:

- `GITHUB_REPO=mauroegp/SmartApp_FW` bzw. `FIRMWARE_GITHUB_REPO`, oder
- feste URL: `FIRMWARE_MANIFEST_URL=https://github.com/mauroegp/SmartApp_FW/releases/download/firmware-v1.0.0/firmware-manifest.json`

Alternativ können Admins `.bin`-Dateien direkt auf dem Server hochladen (Admin → Updates).

## Release veröffentlichen (Maintainer)

Aus dem SmartApp-Hauptrepo nach Build:

```powershell
powershell -ExecutionPolicy Bypass -File scripts\upload-firmware-release.ps1 -Version 1.0.1 -Repo mauroegp/SmartApp_FW
```

Oder manuell:

```bash
gh release create firmware-v1.0.1 firmware-manifest.json *.bin \
  --repo mauroegp/SmartApp_FW --title "Firmware 1.0.1"
```

## License

Firmware-Binaries werden wie im Hauptprojekt SmartApp bereitgestellt. Quellcode-Lizenz siehe [SmartApp](https://github.com/mauroegp/SmartApp).
