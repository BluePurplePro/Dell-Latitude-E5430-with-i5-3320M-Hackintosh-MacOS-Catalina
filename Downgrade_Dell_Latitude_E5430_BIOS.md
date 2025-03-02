# Introduction
This is a step-by-step guide on how to downgrade Dell Latitude E5430 from A21 to A03 BIOS, fixing graphic artifacts/flickering when entering fullscreen mode.

<video src="https://github.com/user-attachments/assets/eac22928-008e-4244-be02-058210d6261d" width="1920" height="1080"></video>

> [!WARNING]
> PROCEED WITH CAUTION!! If you have any concerns about this procedure before following, YOU are choosing to make these modifications. I'm not responsible for bricked devices.

## Prepare the USB
- Take a thumb drive and format it in MS-DOS FAT32 using [rufus](https://rufus.ie/)

![01  Create MS-DOS USB](https://github.com/user-attachments/assets/430ae67d-e52b-48e6-bed1-471ad6407458)

- Download [Dell Latitude E5430 A03 BIOS.zip](https://github.com/user-attachments/files/19036277/Dell.Latitude.E5430.A03.BIOS.zip). After that, copy the BIOS file (vPro or non-Vpro, depending on your laptop) to the thumb drive.

![02  Copy BIOS file into USB](https://github.com/user-attachments/assets/ff5f8e5b-03af-473a-a722-d3eef659e0a9)

- The thum drive should look like this (mine is non-vPro)

![03  BIOS file in USB MS-DOS](https://github.com/user-attachments/assets/47a640f9-e56f-4917-9e74-4753ddffd629)

> [!NOTE]
> More information about A03 BIOS could be found here ([vPro](https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=7pvyc&oscode=biosa&productcode=latitude-e5430) & [non-vPro](https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=c8y58&oscode=biosa&productcode=latitude-e5430))

## Boot from the USB
- Restart the system and press ``F2``. Click ``Load Defaults`` ~> ``OK`` and press Exit

![Load Defaults value BIOS](https://github.com/user-attachments/assets/c080774d-1f8c-4757-8e11-4057f9539aa4)

- After rebooting, press ``F12``. Choose the MS-DOS USB boot

![04  Press F12 and choose MS-DOS USB boot](https://github.com/user-attachments/assets/ad0c95ed-3197-4b45-b488-3a24fc73e321)

- Type the BIOS file in the USB (``5430A03.exe`` or ``5430A03V.exe``)

![05  Type the BIOS file inside the USB](https://github.com/user-attachments/assets/433c669c-cfce-49c3-b25e-18f20cd42828)

- Press ``Y`` to continue

![06  Press Y to continue](https://github.com/user-attachments/assets/7349cb94-e72d-480e-aef4-fbeed2c6ba56)

![07  Let the MS-DOS collect information](https://github.com/user-attachments/assets/6806270d-7999-4a96-bfa2-ed7abce8810d)

- After collecting information, press ``Y`` to confirm and restart

![08  Press Y to confirm and restart](https://github.com/user-attachments/assets/f6c5ccdd-9bcb-4f12-9d48-77118d2fb24e)

- The system will reboot and flash the BIOS. Press ``F3`` to Accept, and then press ``F11`` to Proceed.

![09  Press F3 to Accept](https://github.com/user-attachments/assets/d4647a6a-eedc-4efd-a5ec-13a2fc72e438)

![10  Press F11 to Proceed](https://github.com/user-attachments/assets/43376135-455f-4a3a-a866-89f4736404e7)

- After done flashing, the system will reboot. Press ``F2`` to enter BIOS and change some settings for MacOS

> [!NOTE]
> It is safe to update BIOS to A07. The graphic artifacts/flickering won't come back though

## BIOS Settings (A03)
- **General**
  - Boot Sequence ~> Boot List Option ~> UEFI
- **System Configuration**
  - Intergrated NIC ~> Enabled
  - Parallel Port ~> Disabled
  - Serial Port ~> Disabled
  - SATA Operation ~> AHCI
- **Security**
  - CPU XD Support ~> Enabled
- **POST Behavior**
  - Fastboot ~> Thorough
- **Virtualization Support**
  - Virtualization ~> Enabled
  - VT for Direct I/O ~> Disabled
  - Trusted Execution ~> Disabled


