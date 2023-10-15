# Dell-Latitude-E5430-with-i5-3320M-Hackintosh-MacOS-Catalina
This repository and project hosts the files necessary to boot macOS Catalina successfully on the Dell Latitude E5430 Laptop 
![Dell Latitude E5430](https://github.com/BluePurplePro/Dell-Latitude-E5430-with-i5-3320M-Hackintosh-MacOS-Catalina/assets/84092284/dc9655ca-ae35-4149-9db8-462ecfeacc6c)

# DISCLAIMER
THIS INFORMATION/RESEARCH HAS BEEN DONE AND SHARED PURELY FOR EXPERIMENTAL AND RESEARCH PURPOSES, AND IS IN NO MAY MEANT TO PROMOTE CIRCUMVENTING OF ANYTHING THAT IS SOMEONE ELSE'S CORPORATE PRIVATE PROPERTY. THE INFORMATION LISTED HERE IS PURELY FOR EDUCATIONAL PURPOSES AND SHOULD YOU CHOOSE TO UTILIZE IT IN ANY WAY, I AM IN NO WAY RESPONSIBLE FOR ANY INJUNCTIONS/PROBLEMS THAT MAY OR MAY NOT ARISE AND/OR BE BROUGHT AGAINST ANOTHER FOR THEIR CHOOSING TO HAVE DONE SO.

# Acknowledgements
- https://dortania.github.io/OpenCore-Install-Guide/
  
# Deployment
To deploy this project properly, please obtain the EFI folder from this repository, edit the config.plist to generate new serial number, rom, UUID, etcetera, then save config.plist, and place the files onto the appropriate ESP EFI partition in order to boot using OpenCore bootloader and proceed with your installation of macOS.

# Documentation
_The hardware in this Machine is as follows_:
- CPU: Intel Core i5-4590S
- GPU: Intel(R) HD Graphics 4600
- Mobo: Intel QM77 Chipset
- Drive: Kingston SA400S37 120GB
- TouchPad: Alps Touchpad
- Wifi & Bluetooth: Intel Centrino Wireless-N 1030
- Ethernet: Intel 82579LM Gigabit Network Connection
- Audio: IDT 92HD93BXX + Intel HDMI Output

_What's working_:
- iGPU
- Internal Sound
- Keyboard
- Touchpad
- USB ports
- HDMI output
- Brightness
- Battery Status
- DVD Drive

_Not working_:
- Airplane Mode Switch

_Known issues_:
- Some apps (Safari, Chrome, Spotify, ect) got graphic artifact/flicker when entering fullscreen mode (Except some games like Asphalt 8)

_Not tested_:
- Express Card Expansion
- SD Card Reader (I don't have SD Card lying around)
- VGA Output (I don't have a VGA Monitor)
- Docking Station (Again, I don't have a Docking Station for Dell Latitude E5430)

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
  - VT for Direct I/O ~> Disabled
  - Trusted Execution ~> Disabled
