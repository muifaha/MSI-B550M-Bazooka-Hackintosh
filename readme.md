# OpenCore EFI for AMD Ryzen Hackintosh

## Specification
| **Component** | **Model** |
| ------------- | --------- |
| CPU | AMD Ryzen 5 3600 Overclocked @ 4.2GHz 1.1750v |
| Motherboard | MSI B550M Bazooka |
| RAM | 16GB (2 x 8GB) Corsair Vengeance Overclocked @ 3266MHz |
| Audio Chipset | Realtek® ALC892/ALC897 |
| GPU | XFX RX 5500 XT|
| LAN | Realtek® RTL8111HN 1Gbps LAN controller |
| OS Disk | Transcend SSD SATA3 SSD230S 256GB |

**macOS version**: 11.2.3 (20D91)  
**OpenCore version**: 0.6.8  

## Table of content
 - [Compatible macOS versions](#Compatible-macOS-versions)
 - [Issues](#Issues)
 - [How to use](#How-to-use)
 - [AMD Navi fix](#AMD-Navi-fix)
 - [Sleep informations](#Sleep-informations)
 - [PAT patch information](#PAT-patch-information)
 - [Adobe applications fix](#Adobe-applications-fix)
 - [Spoofing GPU](#Spoofing_GPU)
 - [Guides](#Guides)
 - [Credits](#Credits)

## Compatible macOS versions
 - High Sierra (10.13.x)
 - Mojave (10.14.x)
 - Catalina (10.15.x)
 - Big Sur (11.x)

## Issues
 - Partially-working virtualization (only VirtualBox & Parallels Dekstop 13.1.0 or below)
 - Not working 3.5mm Jack microphone (only USB/Bluetooth microphones)

## How to use
  1. Make your USB installer with [**this guide**](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/)
  2. Clone the repository and paste "BOOT" and "OC" directories into your's pendrive "EFI" folder
  3. Download [**GenSMBIOS**](https://github.com/corpnewt/GenSMBIOS) to generate unique SMBIOS information. Run it and select **Generate SMBIOS**, as the model select **MacPro7,1**
  4. Open config.plist with [**ProperTree**](https://github.com/corpnewt/ProperTree) and go to PlatformInfo > Generic. Set MLB (Board Serial), SystemSerialNumber (Serial) and SystemUUID (SmUUID) to generated values. Change ROM to your network card's MAC address without the `:` character. [**How to get MAC Address?**](https://www.wikihow.com/Find-the-MAC-Address-of-Your-Computer)
  5. Boot it!  
  
If audio does not work for you you have to change layout-id for your audio chipset. Find your codec [**here**](https://github.com/acidanthera/applealc/wiki/supported-codecs) and try setting `alcid` in `boot-args` parameter to every layout-id values from AppleALC wiki  until you get layout-id correct for your motherboard.  

**You CAN NOT use SMBIOS from this repository, it MUST be unique for every macOS installation**

## AMD Navi fix
For AMD Navi GPUs (RX 5500, 5600, 5700) you have to add `agdpmod=pikera` to boot-args to fix black screen issue.

## Sleep informations
In my bluid sleep is work. If not, try to enable `SSDT-SLEEP` in `config.plist`. If you have same USB controllers adresses as me, SSDT should work. If it still does not work you have to find addresses of USB controllers, and modify `SSDT-SLEEP`.  

To modify SSDT use [**MaciASL**](https://github.com/acidanthera/MaciASL). If SSDT does not help read [**Dortania's guide about sleep**](https://dortania.github.io/OpenCore-Post-Install/universal/sleep.html). Remember to try USB mapping.

## PAT patch information
| **Shaneee's** | **Algrey's** |
| ------------- | --------- |
| Much better GPU performance | Worse GPU performance |
| May not work with NVidia GPUs | Compatible with all GPUs | 
| HDMI/DP audio may not work | HDMI/DP audio works | 
| Enabled by default | Disabled by default |

To switch to another patch search for `mtrr_update_action` in `config.plist`. Then set `Enabled` to `true` for patch which you want to use. Remember to set `Enabled` to `false` for second PAT patch.  
Don't try to use them both at the same time, it won't work.

## Adobe applications fix
Adobe applications crash on AMD Hackintoshes due to missing intel_fast_memset instructions. Follow [**this guide**](https://gist.github.com/mikigal/8e1f804fcd7dbafbded2f236653be7c8) to get it working!  

But in Adobe CC 2021 only Photoshop and Illustator need patches, After Effect, Premier Pro, Audition, Character Animation, Media Encoder work without patches.

##Spoofing GPU
In 'config.plist' -> 'DeviceProperties' -> 'Add' -> 'PciRoot(0x0)/Pci(0x3,0x1)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x0,0x0)' i add spoofing XFX 5500XT to Radeon Pro W5500X 8 GB remove 'PciRoot(0x0)/Pci(0x3,0x1)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x0,0x0)' and any childern if you note using RX 5500XT

## Guides
**If you have any problems with installation or booting your macOS, kernel panics or another system related issue check OC configuration guide**  
**If something else isn't working properly (for example USB ports, iServices, DRM/Netflix) check Post-Install guide**
 - Creating USB installer: [**\*click\***](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/)
 - OpenCore configuration: [**\*click\***](https://dortania.github.io/OpenCore-Install-Guide/AMD/zen.html)
 - Post-Install: [**\*click\***](https://dortania.github.io/OpenCore-Post-Install/)
 - Troubleshooting: [**\*click\***](https://dortania.github.io/OpenCore-Post-Install/)
 - ACPI patching: [**\*click\***](https://dortania.github.io/Getting-Started-With-ACPI/)
 - USB mapping: [**\*click\***](https://dortania.github.io/OpenCore-Post-Install/usb/)

If you have any other questions or issues, feel free to ask on [**AMD-OSX Discord**](https://discord.gg/EfCYAJW) or [**Forum**](https://forum.amd-osx.com)

## Cosmetics
**[Guide Change CPU name in Big Sur](https://climbjoe.tv/how-to-change-your-processor-name-in-big-sur/)**
**Guide Change Big SUr Logo in About This Mac**


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

![Screenshot](/screenshot.png?raw=true)
