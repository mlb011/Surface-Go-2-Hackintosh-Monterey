# Surface-Go-2-Hackintosh-Monterey
Stable OpenCore EFI for Microsoft Surface Go 2 (Core m3 / Intel AX200) running macOS Monterey with native graphics, touchscreen, and working Wi-Fi &amp; Bluetooth.
# Microsoft Surface Go 2 – macOS Monterey Hackintosh

OpenCore configuration optimized specifically for running **macOS Monterey (12.x)** on the **Microsoft Surface Go 2 (Intel Core m3-8100Y)** with native graphics acceleration, multi-touch screen support, and working wireless connectivity.

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
| **Graphics Acceleration (QE/CI)** | ✅ Working | Native Intel UHD 615 support on macOS Monterey |
| **Touchscreen** | ✅ Working | Multi-touch gestures supported via `VoodooI2C` |
| **Wi-Fi** | ✅ Working | Native Airport UI via `AirportItlwm.kext` |
| **Bluetooth** | ✅ Working | Full scanning and peripheral pairing via `BlueToolFixup` & `IntelBluetoothFirmware` |
| **USB-C Display Output** | ✅ Working | Supports hot-plugging, screen mirroring, and extended display |
| **Battery Readout** | ✅ Working | Real-time percentage & charging status via `SMCBatteryManager` |
| **MicroSD Card Reader** | ✅ Working | Handled via `RealtekCardReader` |
| **Audio & Headphone Jack** | ✅ Working | Audio output and input working via `AppleALC` |
| **Sleep / Wake** | ⚠️ Partial | Display sleep works normally; deep sleep may fail or hang (see warning below) |
| **AirDrop / AWDL** | ⚠️ Partial/No | Apple-proprietary AWDL is unsupported on Intel AX200 (Use **LocalSend** or **NearDrop**) |
| **Front/Rear Cameras** | ❌ Not working | Intel IPU3 camera sensor is unsupported in macOS |

---

> [!WARNING]
> ### ⚠️ Critical Notice: Sleep / Deep Freeze Issue
> **Deep sleep is unstable.** If the Surface Go 2 enters deep sleep and crashes or shuts down, the device can become completely unresponsive and **extremely difficult to power back on**.  
> * **Recovery:** If stuck, hold the physical Power button for **15 to 20 seconds** to force a hard reset, release, wait 5 seconds, and press Power again until the Microsoft / OpenCore logo appears.
> * **Recommended Workaround:** Go to *System Preferences -> Energy Saver / Battery*, set **Turn display off after:** to your preferred timeout, but uncheck/prevent system sleep. Alternatively, keep an app like **Amphetamine** running to prevent unwanted deep sleep crashes.

---

## 🛠️ Post-Install & Configuration Notes

1. **Generate System Serial Numbers:**  
   Before booting, you must generate your own unique serials under the `MacBookAir9,1` SMBIOS profile using [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS):
   * `SystemSerialNumber`
   * `MLB`
   * `SystemUUID`

2. **On-Screen Accessibility Keyboard:**  
   To use the Surface Go 2 comfortably in tablet mode:
   * Go to *System Preferences -> Accessibility -> Keyboard*.
   * Select the **Accessibility Keyboard** tab and check **Enable Accessibility Keyboard**.

3. **Do NOT Upgrade to macOS Ventura, Sonoma, or Newer:**  
   Apple dropped native driver support for Kaby Lake / Amber Lake-Y graphics after macOS Monterey. Upgrading past Monterey will completely break native GPU acceleration, resulting in heavy UI stutter and rendering glitches unless complex legacy root patches are applied.
