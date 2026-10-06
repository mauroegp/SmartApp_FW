# SmartApp_FW — ESP-Firmware Releases

Öffentliches **Release-only**-Repository für vorkompilierte SmartApp-ESP-Firmware.

- **Dieses Repo:** nur `.bin`-Dateien und `firmware-manifest.json` — kein Firmware-Quellcode
- **Quellcode:** [SmartApp](https://github.com/mauroegp/SmartApp) unter `firmware/`

## Releases

Zwei Kanäle. OTA erkennt ein Update am **SHA256** im Manifest. Die eingebettete Build-Kennung (`1.0.0T1`) ist nur Anzeige.

| Tag | Kanal | Version | Inhalt |
|-----|--------|---------|--------|
| `firmware-v1.0.0` | stable | `1.0.0` | io-4x4, io-8x8, relay-8, heat-8 |
| `firmware-v1.0.0T` | testing (**latest**) | `1.0.0T` | alle übrigen Module |

Updates für Test-Module ersetzen die Assets auf `firmware-v1.0.0T`. Es gibt kein `firmware-v1.0.1`.

### Stable (`firmware-v1.0.0`)

| Modultyp | Datei | Hardware |
|----------|--------|----------|
| `io-4x4` | `io-4x4.bin` | ESP32 Dev Module |
| `io-8x8` | `io-8x8.bin` | ESP32 Dev Module |
| `relay-8` | `relay-8.bin` | ESP32 Dev Module |
| `heat-8` | `heat-8.bin` | ESP32 Dev Module |

### Testing (`firmware-v1.0.0T`)

| Modultyp | Datei | Hardware | Eingebettet |
|----------|--------|----------|-------------|
| `relay-2` | `relay-2.bin` | ESP32 Dev Module | `1.0.0T1` |
| `relay-4` | `relay-4.bin` | ESP32-C3 Super Mini | `1.0.0T1` |
| `relay-16` | `relay-16.bin` | ESP32-C3 + 74HC595 | `1.0.0T1` |
| `io-2x2` | `io-2x2.bin` | ESP32 Dev Module | `1.0.0T1` |
| `gate-2` | `gate-2.bin` | ESP32 Dev Module | `1.0.0T1` |
| `room-panel` | `room-panel.bin` | ESP32 + 3,5″ Touch | `1.0.0T1` |
| `mppt-io` | `mppt-io.bin` | ESP32-C3 Super Mini | `1.0.0T1` |
| `homekit-bridge` | `homekit-bridge.bin` | ESP32-S3 | `1.0.0T1` |
| `rs485-bridge` | `rs485-bridge.bin` | ESP32-S3 | `1.0.0T1` |

## Manifest

Jedes Release enthält **`firmware-manifest.json`** mit Version, SHA256 und Dateiname pro Modultyp.

Die SmartApp-Cloud lädt beide Manifeste und führt sie zusammen. Pro Modul gilt der Eintrag seines Kanals.

- `GITHUB_REPO=mauroegp/SmartApp_FW` bzw. `FIRMWARE_GITHUB_REPO`
- Testing: `https://github.com/mauroegp/SmartApp_FW/releases/download/firmware-v1.0.0T/firmware-manifest.json`
- Stable: `https://github.com/mauroegp/SmartApp_FW/releases/download/firmware-v1.0.0/firmware-manifest.json`

Alternativ können Admins eine `.bin` direkt auf dem Server hochladen (Admin → Updates).

## Release veröffentlichen

Aus dem SmartApp-Hauptrepo, nach dem Build:

```bash
node scripts/build-firmware-module.mjs <modul>
node scripts/promote-firmware-module.mjs <modul>
```

Das Modul landet auf dem Tag seines Kanals (`firmware-v1.0.0` oder `firmware-v1.0.0T`).

## Lizenz

Firmware-Binaries werden wie im Hauptprojekt SmartApp bereitgestellt. Quellcode-Lizenz siehe [SmartApp](https://github.com/mauroegp/SmartApp).