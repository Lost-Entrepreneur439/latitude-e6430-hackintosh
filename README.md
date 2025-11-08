macOS Catalina EFI for the Dell Latitude E6430 using OpenCore. I will try to keep this EFI up to date with the latest OpenCore and kexts

<img width="1366" height="768" alt="Screen Shot 2025-11-08 at 5 03 13 PM" src="https://github.com/user-attachments/assets/012cf68e-6b21-485e-aaeb-a14594d29c9d" />

# WARNING! SMBIOS DETAILS ARE NOT INCLUDED IN THE CONFIG.PLIST.
You will have to use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate a **MacBookPro9,2** SMBIOS for your system, and add them to the config.plist.
Make sure you're on BIOS [A24](https://www.dell.com/support/home/en-ca/drivers/driversdetails?driverid=ng6cn&oscode=biosa&productcode=latitude-e6430) before continuing. Older versions may cause issues

## Other macOS versions?
No. Catalina is the latest supported by MacBookPro9,2, so it's all I'll ever support. If you want a different version, feel free to fork this repo to modify it for whatever version you want. Do note newer versions will likely require OCLP.

## System specs
Do note if your hardware differs, while unlikely, you may have issues.
- CPU: Intel Core i5-3380m
- GPU: Intel HD Graphics 4000
- Chipset: Intel QM77
- Touchpad: ALPS PS/2
- Audio: IDT 92HD93BXX
- Wi-Fi: Dell Wireless 1504
- Ethernet: Intel 82579LM
- Disk: HGST 320GB 7200RPM 2.5"

## Issues:
- Wi-Fi does not work. The BCM4313 chipset used in the E6430's DW1504 is not supported. I'd recommend replacing it with a supported Broadcom card.
- Brightness keys do not work. BrightnessKeys does not support the E6430's configuration.
- Gestures don't work very well.
- VGA doesn't work, macOS hasn't supported VGA since Lion.

If you notice any other problems, please open an issue (or pull request if you have a fix)

### BIOS settings
If you do not set these BIOS settings, macOS will **not** boot.
- General -> Boot Sequence -> UEFI
- General -> Advanced Boot Options -> Uncheck “Enable Legacy Option ROMs”
- System Configuration -> Parallel Port -> Disabled
- System Configuration -> Serial Port -> Disabled
- System Configuration -> SATA Operation -> AHCI
- Security -> CPU XD Support -> Check “Enable CPU XD Support”
- Secure Boot -> Secure Boot Enable -> Disabled
- Performance -> HyperThread control -> Enabled
- POST Behaviour -> Fastboot -> Thorough
- Virtualization Support -> Virtualization -> Check “Enable Intel Virtualization Technology”
- Virtualization Support -> VT for Direct I/O -> Uncheck “Enable VT for Direct I/O”
