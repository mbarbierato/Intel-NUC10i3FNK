[![](https://img.shields.io/badge/Gitter%20HL%20Community-Chat-informational?style=flat&logo=gitter&logoColor=white&color=ed1965)](https://gitter.im/Hackintosh-Life-IT/community)
[![](https://img.shields.io/badge/EFI-Release-informational?style=flat&logo=apple&logoColor=white&color=9debeb)](https://github.com/mbarbierato/Intel-NUC10i3FNK/releases)
[![](https://img.shields.io/badge/Telegram-HackintoshLifeIT-informational?style=flat&logo=telegram&logoColor=white&color=5fb659)](https://t.me/HackintoshLife_it)
[![](https://img.shields.io/badge/Facebook-HackintoshLifeIT-informational?style=flat&logo=facebook&logoColor=white&color=3a4dc9)](https://www.facebook.com/hackintoshlife/)
[![](https://img.shields.io/badge/Instagram-HackintoshLifeIT-informational?style=flat&logo=instagram&logoColor=white&color=8a178a)](https://www.instagram.com/hackintoshlife.it_official/)

# Intel NUC10i3FNK Hackintosh

EFI for Intel NUC10i3/i5/i7 FNK/FNH with OpenCore bootloader

![descrizione](./Screenshot/pc.png)

### Computer Spec:

| Component        | Brank                                  |
| ---------------- | ---------------------------------------|
| CPU              | Intel® Core™ i3-10110U                 |
| iGPU             | Intel® UHD630                          |
| Lan              | Intel I219-V                           |
| Audio            | Realtek ALC256                         |
| Ram              | 8  GB DDR4 2400 Mhz                    |
| Wifi + Bluetooth | Intel® Wireless-AX201 + Bluetooth      |
| Nvme             | Kingston SA400 120GB                   |
| Card Reader.     | SD Card Reader                         |
| SmBios           | MacMini8,1                             |
| BootLoader       | OpenCore                               |

![info](./Screenshot/infomonterey.png)
![info](./Screenshot/info.png)

## Peripherals

![infohack](./Screenshot/hackintooldevice.png)
![infodp2](./Screenshot/DpciScreen2.png)
![infogpu](./Screenshot/hackintooligpu.png)
![usbmap](./Screenshot/mapusb.png)

### What works and What doesn't or WIP:

- [x] Intel® UHD 630 iGPU HDMI/DP Output
- [x] Intel® UHD 630 iGPU - H264 & HEVC
- [x] ALC256 Internal Speakers
- [x] ALC256 Internal Mic
- [x] ALC256 Combojack Headphone
- [ ] ALC256 Combojack Mic
- [x] ALC256 HDMI/DP Audio Output
- [x] All USB Ports 
- [x] SpeedStep / Sleep / Wake
- [x] Intel Lan I219-V10
- [x] Thunderbolt 3 port
- [x] AX 201 Wireless + Bluetooth
- [x] microSDXC Card Reader
- [x] All Sensors (CPU, NVME, SATA, FAN)
- [x] CONTROLLER NVME PciE Gen3x4
- [x] CONTROLLER SATA III (FNH Model)
- [x] HID Key PWRB & SLPB 
- [x] NVRAM
- [x] Windows 10 boot from OpenCore


### BIOS Settings:
To start, choose "Load Defaults" (choose from the menu or press F9 in the BIOS setup).

Then change:
+ Advanced
  - Storage
    * SATA Mode Selection -> AHCI
  - Video
    * IGD Minimum Memory -> 64MB
    * IGD Aperture Size -> 256MB
    * IGD Primary Video Port -> Auto
+ Boot 
  - Secure Boot
    * Secure Boot -> Disabled
  - Boot Priority
    * UEFI Boot -> Checked
    * Legacy Boot -> Unchecked
    * Fast Boot -> Unchecked
+ Power
  - Secondary Power Settings
    * Deep S4/S5 -> On
    * Wake on Lan from S4/S5 -> Stay Off
    * Wake System from S5 -> Off
    * Wake From Thunderbolt Device -> Off


### Special Config:

- Usb port mapping performed
- If have a FNH version, the device path of SD Card is PciRoot(0x0)/Pci(0x1D,0x5)/Pci(0x0,0x0) uncommet on device Properties section and comment PciRoot(0x0)/Pci(0x1D,0x0)/Pci(0x0,0x0)

## CFG Unlock 

N.B. this procedure is very risky.
Any responsibility for this function is discharged to those who perform it.
Be very careful when making this change.

Let's start by downloading the file [RU.efi](./CFGunlock/RU.efi)

We format the USB in FAT32 format.
We copy the RU.efi file in the USB Root.
We enable the UEFI Shell parameter from the BIOS.
We attach the USB stick to the PC and start the UEFI Shell by pressing F10.

If everything is correct, we will come to this screen:

![rootshell](./CFGunlock/rootshell.jpg)

We will then have to find our ROOT, which in my case is FS1
So now we will write "fs1:"
Then we will write "ls"

We will find ourselves in this situation at this point:

![rootshellRU](./CFGunlock/rootshell_RU.jpg)

Then type RU.efi and this mask will appear.

![RU](./CFGunlock/RU.jpg)

Press ALT + ì to remove the popup on the screen.
At this point, on the keyboard, press PagDOWN to scroll the list.

We need to get to the "CPUSetup"

And click ENTER to access the section.

![CPUSetupRU](./CFGunlock/CPUSetupRU.jpg)

Now we have to go down to the value "0030 - 0E

![CPUSetupeMODRU](./CFGunlock/valoremod1.jpg)

Now let's change the value 01 to 00

The correct version will be the following:

![CPUSetupeMODOKRU](./CFGunlock/valoremodok.jpg)

Now to save we press CTRL + W

If everything went well, we will have this screen with a red popup

![CPUSetupeMODSAVERU](./CFGunlock/valoremodsave.jpg)

Enjoy

### SSDT Info
![ssdt](./Screenshot/ssdtscreen.png)

See [ioreg](./macmini.ioreg) for more clarification

## Credits

- [Apple](https://apple.com) for macOS.
- [Intel](https://www.intel.it/content/www/it/it/products/details/nuc.html) for this mini pc.
- [Acidanthera](https://github.com/acidanthera) for OpenCore and all the lovely hackintosh work.
- [Dortania](https://github.com/dortania) For great and detailed guides.
- [Lorys89](https://github.com/Lorys89) For continuos support, patches and sleepless nights.
- [Hackintoshlifeit](https://github.com/Hackintoshlifeit) Support group for installation and post installation.

### If you need help please contact us on [Telegram](https://t.me/HackintoshLife_it)
