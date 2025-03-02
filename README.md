# Dell-Latitude-E5430-Hackintosh
This repository and project hosts the files necessary to boot macOS successfully on the Dell Latitude E5430 Laptop 
![Dell Latitude E5430](https://github.com/BluePurplePro/Dell-Latitude-E5430-with-i5-3320M-Hackintosh-MacOS-Catalina/assets/84092284/dc9655ca-ae35-4149-9db8-462ecfeacc6c)

# DISCLAIMER
THIS INFORMATION/RESEARCH HAS BEEN DONE AND SHARED PURELY FOR EXPERIMENTAL AND RESEARCH PURPOSES, AND IS IN NO MAY MEANT TO PROMOTE CIRCUMVENTING OF ANYTHING THAT IS SOMEONE ELSE'S CORPORATE PRIVATE PROPERTY. THE INFORMATION LISTED HERE IS PURELY FOR EDUCATIONAL PURPOSES AND SHOULD YOU CHOOSE TO UTILIZE IT IN ANY WAY, I AM IN NO WAY RESPONSIBLE FOR ANY INJUNCTIONS/PROBLEMS THAT MAY OR MAY NOT ARISE AND/OR BE BROUGHT AGAINST ANOTHER FOR THEIR CHOOSING TO HAVE DONE SO.

# Acknowledgements
- Acidanthera for [OpenCore Bootloader](https://github.com/acidanthera/OpenCorePkg)
- Dortania for [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide)
- Corpnewt for [SSDT Time](https://github.com/corpnewt/SSDTTime)
- USBToolbox for [USBToolbox](https://github.com/USBToolBox)
- And many more awesome people in the hackintosh community
  
# Deployment
To deploy this project properly, please obtain the EFI folder from this repository, edit the config.plist to generate new serial number, rom, UUID, etcetera, then save config.plist, and place the files onto the appropriate ESP EFI partition in order to boot using OpenCore bootloader and proceed with your installation of macOS.

# BIOS Settings (A21 BIOS)
- **General**
  - Boot Sequence ~> Boot List Option ~> UEFI
- **System Configuration**
  - Intergrated NIC ~> Enabled
  - Parallel Port ~> Disabled
  - Serial Port ~> Disabled
  - SATA Operation ~> AHCI
- **Security**
  - CPU XD Support ~> Enabled
- **Secure Boot**
  - Secure Boot Enable ~> Disabled
- **POST Behavior**
  - Fastboot ~> Thorough
- **Virtualization Support**
  - Virtualization ~> Enabled
  - VT for Direct I/O ~> Disabled
  - Trusted Execution ~> Disabled
> [!NOTE]
> ``VT for Direct I/O`` could be enabled if ``DisableIoMapper`` (under Kernel ~> Quirk) is Enabled

# Hardware
- The hardware in this Machine is as follows:
  - CPU: Intel Core i5-3320M
  - GPU: Intel(R) HD Graphics 4000
  - Display Resolution: 1366x768
  - Mobo: Dell 04V77Y Rev. A00
  - SATA Drive: Kingston SA400S37 120GB
  - DVD Drive: MATSHITA DVD+-RW UJ8D1
  - Keyboard & TouchPad: PS2 Keyboard & PS2 Alps Touchpad
  - Wifi & Bluetooth: Intel Centrino Wireless-N 1030
  - Ethernet: Intel 82579LM Gigabit Network Connection
  - Audio: IDT 92HD93BXX + Intel HDMI Output
  - BIOS version: A21
- Click [here](https://www.dell.com/support/manuals/en-us/latitude-e5430/delllatitudee5430_om-v1/specifications?guid=guid-dc451241-36f9-4f68-bf76-de4751505456&lang=en-us) for more information about the specifications

# Drivers & Essential Kernel Extensions
| Required Drivers | 
| ------------- | 
| [HfsPlus.efi](https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi) |
| [OpenRuntime.efi](https://github.com/acidanthera/OpenCorePkg) |

| Essential Kexts |
| ------------- |
| [Lilu.kext](https://github.com/acidanthera/Lilu) |
| [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC) |

# Kernel Extensions corresponding to hardware
| Hardware  | Kext(s) |
| ------------- | ------------- |
| Intel(R) HD Graphics 4000 | [Whatevergreen.kext](https://github.com/acidanthera/WhateverGreen)  |
| Keyboard & Touchpad | [VoodooPS2Controller.kext](https://github.com/acidanthera/VoodooPS2)  |
| Intel 82579LM Gigabit Network Connection  | [IntelMausi.kext](https://github.com/acidanthera/IntelMausi) |
| Intel Wifi | [AirportItlwm.kext](https://github.com/OpenIntelWireless/itlwm) |
| Intel Bluetooth (from MacOS10.13 to MacOS11) | [IntelBluetoothFirmware.kext; IntelBTPatcher.kext; IntelBluetoothInjector.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) |
| Intel Bluetooth (MacOS 12 and newer) | [IntelBluetoothFirmware.kext; IntelBTPatcher.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) & [BlueToolFixup.kext](https://github.com/acidanthera/BrcmPatchRAM)|
| IDT 92HD93BXX  | [AppleALC.kext](https://github.com/acidanthera/AppleALC) with layoutid ``12`` |

> [!IMPORTANT]
> Display with 1600x900 resolution have to change ``AAPL,ig-platform-id`` value to ``04006601`` in DeviceProperties ~> Add ~> PciRoot(0x0)/Pci(0x2,0x0)

# Result
## Working:
- iGPU
- Wifi & Bluetooth
- Internal Sound
- Keyboard
- Touchpad
- HDMI output
- Brightness
- Battery Status
- DVD Drive

## Partially working:
- Sleep
- USB ports (the USB 2.0 port next to the 3.5mm Audio Jack in my laptop is broken)
> [!NOTE]
> It is necessary to re-map USB using [USBToolBox](https://github.com/USBToolBox/tool), since the USB 2.0 port next to the 3.5mm Audio Jack in my laptop is broken

## Known issue(s):
- Some apps like Chess.app, Safari.app, etc got graphic artifacts/flickering when entering fullscreen mode
<video src="https://github.com/user-attachments/assets/eac22928-008e-4244-be02-058210d6261d" width="1920" height="1080"></video>

> [!NOTE]
> [Downgrading the BIOS to A03](https://github.com/BluePurplePro/Dell-Latitude-E5430-Hackintosh/blob/main/Downgrade_Dell_Latitude_E5430_BIOS.md) will fix graphic artifacts/flickering issue.

## Not working:
- Airplane Mode Switch
- Airdrop (Intel Wireless)
- VGA Output (Analog)
- AppleIntelPowerManagement (CFG Lock)
> [!NOTE]
> Follow [this guide](https://github.com/BluePurplePro/Disable-CFG-Lock-Dell-Machines) to turn off CFG-Lock on Dell Latitude E5430

_Not tested_:
- Express Card Expansion
- SD Card Reader (Mine is broken)
- Docking Station (I don't have a Docking Station for Dell Latitude E5430)
- SIM Slot (I don't have a WWAN Card, although [some one does make it work in MacOS though](https://github.com/xmm7360/xmm7360-usb-modeswitch))
