# Surface-Go-2-Hackintosh-Monterey
Stable OpenCore EFI for Microsoft Surface Go 2 (Core m3 / Intel AX200) running macOS Monterey with native graphics, touchscreen, and working Wi-Fi &amp; Bluetooth.
# Microsoft Surface Go 2 – macOS Monterey Hackintosh

OpenCore configuration optimized specifically for running **macOS Monterey (12.x)** on the **Microsoft Surface Go 2 (Intel Core m3-8100Y)** with full native graphics acceleration, tactile support, and working wireless connectivity.

---

## 💻 Hardware Specifications

| Component | Hardware Model |
| :--- | :--- |
| **CPU** | Intel Core m3-8100Y (Amber Lake-Y) |
| **GPU** | Intel UHD Graphics 615 |
| **Display** | 10.5" PixelSense (1920 x 1280), Multi-touch |
| **Wi-Fi** | Intel Wi-Fi 6 AX200 |
| **Bluetooth** | Intel AX200 Bluetooth 5.1 |
| **Storage** | 128GB NVMe SSD |
| **Bootloader** | OpenCore |

---

## 📊 Status / What Works

| Feature | Status | Notes |
| :--- | :---: | :--- |
| **Graphics Acceleration (QE/CI)** | ✅ Working | Full native Intel HD 615 support on macOS Monterey |
| **Touchscreen** | ✅ Working | Multi-touch gesture support via VoodooI2C |
| **Wi-Fi** | ✅ Working | Native Airport UI via `AirportItlwm.kext` |
| **Bluetooth** | ✅ Working | Functional pairing and peripheral support via `BlueToolFixup` & `IntelBluetoothFirmware` |
| **USB-C Display Output** | ✅ Working | Hot-plug and mirror/extend display support |
| **Battery Readout** | ✅ Working | Real-time percentage & AC status via `SMCBatteryManager` |
| **MicroSD Card Reader** | ✅ Working | Handled via `RealtekCardReader` |
| **Audio & Headphone Jack** | ✅ Working | AppleALC |
| **AirDrop / AWDL** | ⚠️ Partial/No | Apple-proprietary AWDL is not supported on Intel AX200 (Use **LocalSend** or **NearDrop**) |
| **Front/Rear Cameras** | ❌ Not working | Intel IPU3 sensor is unsupported in macOS |

---

## ⚠️ Important Post-Install Notes

1. **Serial Numbers:** Remember to generate your own `SystemSerialNumber`, `MLB`, and `SystemUUID` using GenSMBIOS under the `MacBookAir9,1` profile before booting.
2. **On-Screen Keyboard:** Navigate to *System Preferences -> Accessibility -> Keyboard -> Accessibility Keyboard* to enable the virtual tablet keyboard.
3. **OS Updates:** Do **not** upgrade past macOS Monterey (such as Ventura, Sonoma, or newer) through System Preferences. Newer macOS versions drop native driver support for Kaby Lake / Amber Lake-Y GPUs and require complex legacy root patches.
