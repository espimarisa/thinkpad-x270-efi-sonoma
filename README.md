# 🍎 ThinkPad X270 EFI - Sonoma

This is my OpenCore EFI configured to run **macOS Sonoma** on my Lenovo ThinkPad X270.

<p align="center">
  <img src="https://github.com/espimarisa/thinkpad-x270-efi-sonoma/assets/49253425/c8924f74-b111-4314-b6cf-6dc54815db4d">
</p>

<details>
<summary><strong>💻 My hardware</strong></summary>

<br />

| Category  | Component                         |
| --------- | --------------------------------- |
| CPU       | Intel Core i7-7500U               |
| GPU       | Intel HD 620 Graphics             |
| RAM       | 32GB DDR4 @ 2133MHz               |
| SSD       | 1TB Crucial MX500 SATA SSD        |
| Display   | 12.5" 1920x1080 FHD IPS           |
| Ethernet  | Intel i219-V Ethernet             |
| WiFI + BT | Intel AX210 (originally AC8265)   |
| Audio     | Realtek ALC3268 (ALC298)          |
| Keyboard  | Backlit Lite-On keyboard          |
| Battery   | Internal 3-cell + external 6-cell |
| WWAN      | Sierra Wireless EM7455 LTE        |

</details>

## ⚠️ Warning

This EFI is only meant for the Lenovo ThinkPad X270. I am NOT responsible for any harm caused to your device or mental health caused by attempting a Hackintosh. You have been warned.

In order to get iServices and other functionality working, you must fill in your own MLB, ROM, Serial, and UUID information. You can do so by using [GenSMBios][gensmbios] and using the SMBIOS for a `MacBookPro15,2`.

## ✨ Status

### ✅ Working

- [x] iServices
- [x] Handoff
- [x] FileVault
- [x] Sleep/wake
- [x] HDMI output
- [x] Backlight control
- [x] Keyboard hotkeys
- [x] Battery information
- [x] Power management
- [x] Graphics acceleration
- [x] Boot chime and GUI picker
- [x] Audio, speakers, and headphone jack
- [x] Ethernet and WiFi/Bluetooth (w/ Heliport)
- [x] TrackPad and TrackPoint with full gestures
- [x] Realtek SD Card Reader (not heavily tested)
- [x] USB ports, USB mapping, and dock USB ports

### ❌ Not working

- [ ] Native WiFi control / AirportItlwm
- [ ] [Safari DRM][drm-note] (use Chrome for DRM playback)
- [ ] Fingerprint reader (no driver actually exists)
- [ ] WWAN ([driver exists][wwan-driver] but is not working)

### ⚠️ Untested

- [ ] Apple SideCar
- [ ] Apple Watch Unlock
- [ ] Dock video output
- [ ] Dock headphone jack

## 🛠️ Post-install tweaks

I recommend doing the following to get your system as smooth as possible:

1. Install [HeliPort][heliport] for WiFi control until AirportItlwm works with Sonoma
2. Enable Tap to Click in System Settings -> Trackpad 🙄
3. Disable hibernation, powernap, and some other power settings

   ```sh
    sudo pmset autopoweroff 0
    sudo pmset powernap 0
    sudo pmset standby 0
    sudo pmset proximitywake 0
    sudo pmset tcpkeepalive 0
   ```

4. If you're running a 1080p internal display, check out [BetterDisplay][betterdisplay] and run 1280x720@2x for HiDPI support
5. Use [Boom 2][boom2] to boost the speaker output as by default it's quite quiet. Note that this is not a free application!

[gensmbios]: https://github.com/corpnewt/GenSMBIOS "A link to GenSMBIOS"
[drm-note]: https://dortania.github.io/OpenCore-Post-Install/universal/drm.html#fixing-drm-support-and-igpu-performance "A link to the OpenCore Post-Install guide note on Safari DRM"
[wwan-driver]: https://github.com/KirisameR/Sierra-Wireless-EM74xx-Series-WWAN-Card-Driver-for-macOS-Catalina "A link to the Sierra Wireless kext"
[heliport]: https://github.com/OpenIntelWireless/HeliPort "A link to Heliport"
[betterdisplay]: https://github.com/waydabber/BetterDisplay "A link to BetterDisplay"
[boom2]: https://www.globaldelight.com/boom2/ "A link to boom2"
