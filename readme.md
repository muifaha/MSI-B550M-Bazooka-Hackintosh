# OpenCore EFI for AMD Ryzen Hackintosh

![Dark mode](https://raw.githubusercontent.com/muifaha/MSI-B550M-Bazooka-Hackintosh/main/images/Screen%20Shot%202021-04-09%20at%2021.32.04.png)

## Specification
| **Component** | **Model** |
| ------------- | --------- |
| CPU | AMD Ryzen 5 3600 Overclocked @ 4.2GHz 1.1750v |
| Motherboard | MSI B550M Bazooka |
| RAM | 16GB (2 x 8GB) Corsair Vengeance Overclocked @ 3266MHz |
| Audio Chipset | Realtek® ALC892/ALC897 |
| GPU | XFX RX 5500 XT 8GB|
| LAN | Realtek® RTL8111HN 1Gbps LAN controller |
| OS Disk | Transcend SSD SATA3 SSD230S 256GB |

**macOS version**: 11.5
**OpenCore version**: 0.7.1  

ACPI SSDT's​
- SSDT-USBX (USB power tables)
- SSDT-PLUG (CPU power management)
- SSDT-SBRG (Correcting EC, RTC memory & IRQ conflicts)
- SSDT-SBUS-MCHC (SMBus Support)
- SSDT-CPUR


## Credits
**Software:**
 - [[Bootloader] OpenCore](https://github.com/acidanthera/OpenCorePkg)
 - [[Resources] Picker GUI](https://github.com/acidanthera/OcBinaryData/tree/master/Resources)
 - [[Patch] AMD_Vanilla](https://github.com/AMD-OSX/AMD_Vanilla)
 - [[SSDT] EC-USBX-DESKTOP](https://github.com/dortania/Getting-Started-With-ACPI/blob/master/extra-files/compiled/SSDT-EC-USBX-DESKTOP.aml)
 - [[Driver] OpenRuntime](https://github.com/acidanthera/OpenCorePkg)
 - [[Driver] OpenCanopy](https://github.com/acidanthera/OpenCorePkg)
 - [[Driver] OpenHfsPlus](https://github.com/acidanthera/OpenCorePkg)
 - [[Kext] Lilu](https://github.com/acidanthera/Lilu)
 - [[Kext] VirtualSMC](https://github.com/acidanthera/VirtualSMC)
 - [[Kext] WhateverGreen](https://github.com/acidanthera/WhateverGreen)
 - [[Kext] AppleALC](https://github.com/acidanthera/AppleALC)
 - [[Kext] RealtekRTL8111](https://github.com/Mieze/RTL8111_driver_for_OS_X)
 - [[Kext] AMDRyzenCPUPowerManagement](https://github.com/trulyspinach/SMCAMDProcessor)
 - [[Kext] SMCAMDProcessor](https://github.com/trulyspinach/SMCAMDProcessor)
 - [[Kext] NVMeFix](https://github.com/acidanthera/NVMeFix)
 - [[Kext] AppleMCEReporterDisabler](https://github.com/AMD-OSX/AMD_Vanilla/blob/opencore/Extra/AppleMCEReporterDisabler.kext.zip)
 - [[Kext] HoRNDIS](https://github.com/jwise/HoRNDIS)    

 **People:**
 - [Apple](https://apple.com) for macOS
 - [AMD-OSX Developers](https://github.com/AMD-OSX) for kernel patches for AMD CPUs
 - [Acidanthera](https://github.com/acidanthera) for OpenCore and most of used kexts
 - [Trulyspinach](https://github.com/trulyspinach) for Ryzen power management and monitoring kexts
 - [Mieze](https://github.com/Mieze) for RealtekRTL8111 kext
 - [Dortania](https://github.com/dortania) for OpenCore configuration guides
 - [XLNC](https://github.com/naveenkrdy) for Adobe patches for AMD CPUs
 - [AMD-OSX Community](https://amd-osx.com) for support while making my Hackintosh
<br>
