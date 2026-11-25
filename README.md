# Fujitsu Stylistic Q616 — OpenCore EFI

OpenCore EFI configuration built and tested on a **Fujitsu Stylistic Q616** tablet PC, including GPU spoofing / graphics patches to run newer x86 macOS versions (such as macOS Sequoia) alongside older releases.

support Big Sur - Tahoe [Error sleep and shutdown on Tahoe olny]
<img width="1920" height="1080" alt="lol" src="https://github.com/user-attachments/assets/af758bad-4688-4fae-bf32-0bd22160c364" />

> ⚠️ **Important:** Generate your own **SMBIOS** (`SerialNumber`, `MLB`, `SmUUID`, `ROM`) before booting. Do not use placeholder or reused serials with an Apple ID.

---

## Hardware Specifications (Test Rig)

* **Device:** Fujitsu Stylistic Q616 (Tablet PC, no internal battery)
* **CPU:** Intel Core m3 (Skylake dual-core)
* **iGPU:** Intel HD Graphics 515 (patched / spoofed for hardware acceleration)

---

## Tested macOS Versions

* **macOS Sequoia (e.g. 15.8.3):** Boots and runs with graphics acceleration enabled (no 7MB fallback).
* **macOS Tahoe:** Boots and reaches the desktop, though UI effects can feel heavy on 4 GB RAM and dual-core Core m3 hardware.
---

## What Works & What Doesn't

### Working
* Graphics acceleration on Intel HD Graphics 515 (1536 MB VRAM allocation in macOS)
* Built-in microphone (configured/enabled)
* Basic display output and system boot via OpenCore

### Issues / To Verify
* **UI performance on newer/heavier macOS:** Heavy transparency and animations may lag due to 4 GB RAM and low-power Core m3 limits.
* **Battery status:** The test unit has no internal battery; battery reporting/ACPI patches should be verified on units with a working battery.
* **Touchscreen / Pen / Sensors / Wi-Fi & Bluetooth:** Verify behavior on your exact hardware revision and wireless card.

---

## Setup Instructions

1. Download the EFI `.zip` archive from the **Releases** page and extract the `EFI` folder.
2. Open `EFI/OC/config.plist` using **ProperTree** or **OCAuxiliaryTools**.
3. Use **GenSMBIOS** to generate fresh SMBIOS values matching your target `System Product Name` (e.g. `MacBookPro13,1` or `MacBookPro15,1`), and fill in:
   * `System Serial Number` (`SerialNumber`)
   * `MLB` (`Board Serial Number`)
   * `System UUID` (`SmUUID`)
   * `ROM`
4. Copy the `EFI` folder to the **EFI** partition of your USB installer or internal drive.
5. Reset NVRAM at the OpenCore picker if switching SMBIOS or updating `config.plist`.

---

## Disclaimer & Credits

This EFI is shared as-is for experimentation and reference on niche hardware. Always keep a backup EFI on a USB drive before testing changes.

* **OpenCore & Kexts:** Acidanthera and the Hackintosh / Dortania community.
