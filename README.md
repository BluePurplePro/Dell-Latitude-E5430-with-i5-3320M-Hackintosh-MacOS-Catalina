# Dell-Latitude-E5430-with-i5-3320M-Hackintosh-MacOS-Catalina
This repository and project hosts the files necessary to boot macOS Catalina successfully on the Dell Latitude E5430 Laptop 
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

# Documentation
_The hardware in this Machine is as follows_:
- CPU: Intel Core i5-3320M
- GPU: Intel(R) HD Graphics 4000
- Monitor resolution: 1366x768
- Mobo: Intel QM77 Chipset
- Drive: Kingston SA400S37 120GB
- Keyboard & TouchPad: PS2 Keyboard & PS2 Alps Touchpad
- Wifi & Bluetooth: Intel Centrino Wireless-N 1030
- Ethernet: Intel 82579LM Gigabit Network Connection
- Audio: IDT 92HD93BXX + Intel HDMI Output

# Drivers & Essential Kernel Extensions
| Required Drivers | Essential Kexts |
| ------------- | ------------- |
| [HfsPlus.efi](https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi) | [Lilu.kext](https://github.com/acidanthera/Lilu) |
| [OpenRuntime.efi](https://github.com/acidanthera/OpenCorePkg) | [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC) |

# Kernel Extensions corresponding to hardware
| Hardware  | Kext(s) |
| ------------- | ------------- |
| Intel(R) HD Graphics 4000 | [Whatevergreen.kext](https://github.com/acidanthera/WhateverGreen)  |
| Keyboard & Touchpad | [VoodooPS2Controller.kext](https://github.com/acidanthera/VoodooPS2)  |
| Intel 82579LM Gigabit Network Connection  | [IntelMausi.kext](https://github.com/acidanthera/IntelMausi) |
| Intel Wifi | [AirportItlwm.kext](https://github.com/OpenIntelWireless/itlwm) |
| Intel Bluetooth | [IntelBluetoothFirmware.kext; IntelBTPatcher.kext; IntelBluetoothInjector.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) |
| IDT 92HD93BXX  | [AppleALC.kext](https://github.com/acidanthera/AppleALC)  |

> [!IMPORTANT]
> For 1600x900 monitor, go to DeviceProperties ~> Add ~> PciRoot(0x0)/Pci(0x2,0x0) and change ``AAPL,ig-platform-id`` value to ``04006601`` 

# Result
_Working_:
- iGPU
- Wifi & Bluetooth
- Internal Sound
- Keyboard
- Touchpad
- HDMI output
- Brightness
- Battery Status
- DVD Drive

_Partially working_:
- Sleep
- USB ports
> [!NOTE]
> My USB 2.0 port (near the 3.5mm Audio Jack) is broken, be sure to map your using [USBToolBox](https://github.com/USBToolBox/tool)

_Not working_:
- Airplane Mode Switch
- Airdrop
- VGA Output

_Not tested_:
- Express Card Expansion
- SD Card Reader (I don't have SD Card lying around)
- Docking Station (Again, I don't have a Docking Station for Dell Latitude E5430)
- SIM Slot (SIM Card might not work in MacOS)

_Known issues_:
- Some apps (Safari, Chrome, Spotify, ect) got graphic artifact/flicker when entering fullscreen mode (Asphalt 8 is the exception)

# BIOS Settings
- **General**
  - Boot Sequence ~> Boot List Option ~> UEFI
  - Advanced Boot Options ~> Enable Legacy Option ROMs ~> Disabled
- **System Configuration**
  - Intergrated NIC ~> Enabled
  - Parallel Port ~> Disabled
  - Serial Port ~> Disabled
  - SATA Operation ~> AHCI
- **Security**
  - TPM Security ~> Disabled
  - CPU XD Support ~> Enabled
- **Secure Boot**
  - Secure Boot Enable ~> Disabled
  - Expert key Management ~> Enable Custom Mode ~> Disabled
- **Performance**
  - Multi Core Support ~> All
  - Intel SpeedStep ~> Enabled
  - C-States Control ~> Enabled
  - Intel TurboBoost ~> Enabled
  - HyperThread control ~> Enabled
- **POST Behavior**
  - Fastboot ~> Thorough
- **Virtualization Support**
  - Virtualization ~> Enabled
  - Trusted Execution ~> Disabled
  - VT for Direct I/O ~> Disabled
> [!NOTE]
> ``VT for Direct I/O`` could be enabled if ``DisableIoMapper`` (under Kernel ~> Quirk) is Enabled
  
