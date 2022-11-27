# Gigabyte B550 Gaming X V2 - OpenCore Hackintosh

![Logo](https://static.gigabyte.com/StaticFile/Image/Global/76e3dbf92fc24582dafd2ec94e348800/Product/25898/png/1000)

**LEGAL DISCLAIMER:**

I am not responsible for any data loss, hardware faults or copyright infringements caused by using this EFI on your system, use at your own discretion, by downloading and using this software you take full responsibilty for your own actions. 

## Introduction
[![OpenCore](https://img.shields.io/badge/OpenCore-0.8.6-blue.svg)](https://github.com/acidanthera/OpenCorePkg) 

[![macOS-Stable](https://img.shields.io/badge/macOS-13.0.1-brightgreen.svg)](https://www.apple.com/macos/ventura)

This is not a guide but a reference for the Gigabyte B550 Gaming X V2, you should be able to simply copy the EFI folder into your EFI Partition and start working with macOS installers, prior to installation you ***must*** generate an SMBIOS/SystemUUID for a MacPro7,1 into the *config.plist* file, keep in mind that any additional hardware such was Nvidia graphics cards, non-Apple broadcom-based Wi-Fi adaptors and other PCIe cards may cause issues and prevent macOS from booting or installing correctly, if you are having issues remove all additional components from your board and make sure the UEFI/BIOS is configured correctly. 

If you find any issues or bugs please let me know by submitting an issue or request, I will look into it and see what I can do to help also you can also find almost anything you need on [TonyMacX86](https://www.tonymacx86.com) and the Hackintosh [Reddit](https://www.reddit.com/r/hackintosh/) site.
## Before installation
#### Generate your own SMBIOS
Download and use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to create your own system serial number and SystemUUID based on the MacPro7,1.
#### Use the correct AMD Ryzen configuration
Review the documentation at [Ryzen and Threadripper (17h and 19h)](https://dortania.github.io/OpenCore-Install-Guide/AMD/zen.html) and update to the correct values that match your AMD Ryzen CPU, this is currently set to 6-core / 12 threads for my AMD Ryzen 5 5500 but should work for any 6-core / 12 thread Ryzen chip that is Zen2/Zen3 but treat that with a grain of salt.
#### Current Stable Update: [![BIOS](https://img.shields.io/badge/BIOS-F15-lightgrey)](https://download.gigabyte.com/FileList/BIOS/mb_bios_b550-gaming-x-v2_f15.zip)
#### UEFI configuration
> These options listed below MUST be configured as is unless advised as optional.
- Save & Exit 
  - **Load Optimized Defaults** *(required)*
- Tweaker
  - Advanced CPU 
      - Core Performance Boost
        - **Auto** *(required)*
      - SVM Mode
        - **Enabled** *(optional)* Only enable if you want virtualisation for Parallels / Virtualbox etc
      - SMT Mode
        - **Auto** *(required)* 
  - Extreme Memory Profile (X.M.P.)
      - **Profile 1** *(required)*
- Settings
  - Platform Power
    - AC BACK
      - **Always Off** *(required)*
    - Power On By Keyboard
      - **Disabled** *(required)*
    - Power On By Mouse
      - **Disabled** *(required)*
    - Wake on LAN
      - **Disabled** *(required)*
    - CEC 2019 Ready
      - **Disabled** *(required)*
  - IO Ports
      - USB Configuration
        - Legacy USB Support
          - **Enabled** *(required)*
        - XCHI Hand-off
          - **Enabled** *(required)*
  - Sata Configuration
    - SATA Mode
      - **ACHI** *(required)*
    - NVMe RAID mode
      - **Disabled** *(required)*
  - Miscelanous
    - PCIEX16 Solot configuration
      - **Auto** *(required)*
    - PCIe Slot Configuration
      - **Auto** *(required)*
    - 3DMark01 EnhanceMent
      - **Disabled** *(optional)*
    - IOMMU
      - **Disabled** *(required)*
    - AMD CPU fTPM
      - **Enabled** *(required)*
  - Boot
    - Fast Boot
      - **Disabled** *(required)*
    - CSM Support
      - **Disabled** *(required)*
    - Secure Boot
      - **Disabled** *(required)*
- Save Settings and exit.
## Current State
#### Working
- [x]  AMD Ryzen 5 & AMD Radeon RX580
- [x]  AppStore, FaceTime, iMessage and the iTunes Store. `SMBIOS is required for this`
- [x]  Booting Linux EFI from OpenCore.
- [x]  Booting Linux Live USB from OpenCore.
- [x]  EFI Graphical Boot Menu
- [x]  Onboard Realtek Ethernet (RTL8111).
- [x]  Output audio jacks `Front and rear panel.`
- [x]  Shutdown / Restart / Sleep
- [x]  Sidecar.
- [x]  USB 2.0 & 3.0  `Front and rear panel.`
#### Not Working
- [ ]  Boot chime.
- [ ]  Input audio jacks `This appears to be a bug with AMD/Realtek audio and no fixes have been placed as of yet.`
#### Untested
- [ ]  FileVault
#### My Hardware Configuration
|Category   |Component                                                    |Note                                                                                                                 |
|-----------|-------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
|Motherboard|Gigabyte Gaming X V2                      |[![BIOS](https://img.shields.io/badge/BIOS-F15-lightgrey)](https://download.gigabyte.com/FileList/BIOS/mb_bios_b550-gaming-x-v2_f15.zip)|
|CPU        |AMD Ryzen 5 5500 - (6-core / 12 threads)  ||
|GPU        |AMD Radeon RX580 - 8GB (Sapphire Nitro+)  |Follow the official [Apple supported GPU list](https://support.apple.com/en-nz/HT208544) if you'd like plug and play.                   |
|Memory     |Crucial Ballistix 32GB (DDR4 2666Mhz)     ||
|Ethernet   |Realtek RTL8111                           ||
|WI-FI & BT |Fenvi FV-T919                             |Enables AirDrop, AirPlay and Wi-Fi natively without any additional Kexts                                                                |
|NVME 1     |Samsung 980 Pro - 1TB                     |macOS Boot drive                                                                                                                        |
|NVME 2     |Samsung 980 Pro - 1TB                     |Windows Boot Drive                                                                                                                      |
|Hard Disk 1|Seagate IronWolf Pro - 8TB                |Mirrored Raid-1: Data Storage Drive                                                                                                     |
|Hard Disk 2|Seagate IronWolf Pro - 8TB                |Mirrored Raid-1: Data Storage Drive                                                                                                     |
|Hard Disk 3|Seagate Iron Wolf Pro - 4TB               |Time Machine backups                                                                                                                    |
|Hard Disk 4|Seagate Iron Wolf Pro - 2TB               |Test drive for system upgrades and beta EFI testing                                                                                     |

## Change log
- **26 November 2022**
  - Hello world!
