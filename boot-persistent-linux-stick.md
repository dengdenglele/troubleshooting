# Make any external drive with fully installed Linux bootable
Linux distributions can be installed on USB thumb drives.
Data is persistent and thumb drive can be plugged into different host devices.

## Issue
- Some distros do not boot without issues or changes in BIOS/UEFI
- Problematic distros:
  - Debian
  - Kali
  - Maybe more...

## Solution
- A full disk installation of Ubuntu (on an internal or external device) creates an bootloader structure which can be used universally on any external device
- This bootloader structure can be copied to "problematic" distros and used after modifications
- It might be necessary to mount `efi` partition, otherwise `/boot/efi` directory stays empty
- The `efi` partition is usually the very first partition on a hard drive

```bash
cd /boot/efi/EFI
ls -l BOOT/ ubuntu/
BOOT/:
total 1876
-rwx------ 1 root root 966664 Aug 21 22:23 BOOTX64.EFI
-rwx------ 1 root root  88344 Aug 21 22:23 fbx64.efi
-rwx------ 1 root root 856280 Aug 21 22:23 mmx64.efi

ubuntu/:
total 4392
-rwx------ 1 root root     108 Aug 21 22:23 BOOTX64.CSV
-rwx------ 1 root root     121 Aug 21 22:23 grub.cfg
-rwx------ 1 root root 2656136 Aug 21 22:23 grubx64.efi
-rwx------ 1 root root  856280 Aug 21 22:23 mmx64.efi
-rwx------ 1 root root  966664 Aug 21 22:23 shimx64.efi
```

- BOTH directories, `/boot/efi/EFI/BOOT/` and `/boot/efi/EFI/ubuntu/`, must be copied to "problematic" distro
- The `.EFI and .efi` files in both `/boot/efi/EFI/BOOT/` and `/boot/efi/EFI/ubuntu/` are binary files and must not be changed or deleted
- The name of the directory `/boot/efi/EFI/ubuntu/` can be changed into something else e.g. `/boot/efi/EFI/kali/` or `/boot/efi/EFI/debian/`
- Change to root user `sudo su`
- Within `/boot/efi/EFI/ubuntu/grub.cfg` **the existing UUID must be changed** to the UUID of the `/boot` of the other distro
  - Use `lsblk -f` or `sudo blkid` to identify the **new UUID** of `/boot`
  - Output first line: search.fs_uuid **"insert-the-new-UUID-here"** root
- Open `/boot/efi/EFI/ubuntu/BOOTX64.CSV` with LibreOffice or VSCode
  - Output first line: shimx64.efi,**Ubuntu**,,This is the boot entry for ubuntu
  - It might be neccesary to copy `BOOTX64.CSV` somewhere else (copy to `/home/user/`) and adapt ownership (`sudo chown user:user /home/user/BOOTX64.CSV`) before changes can be made
  - Use LibreOffice or VSCode or VSCodium to make changes (OnlyOffice behaves strangly, unable to identify what `^@` is)
  - The boot entry (second field) for the BIOS can be changed, e.g. change "Ubuntu" to "Kali Linux", "Linux Mint" etc. (spaces are allowed)
  - The last field allows to write a description (optional)
  - After changes were made, check `BOOTX64.CSV` with `nano` (`vi` does not display `^@`, if file content starts with strange characters) and delete "strange" characters (o^@k^@a^@y^@ is okay) at the beginning of the file (first line) when saved with LibreOffice or VSCode
 
## Revert changes
```bash
sudo grub-install # reverts the changes in /boot/efi/EFI/<distro-name>/
sudo update-grub # reload config based on changes in /etc/default/grub
```

## Warnings
- Do not try this approach, when Windows 10 is installed on the same disk (not checked for Windows 11 yet)
- BIOS/UEFI will first look in the `/boot/efi/EFI/Microsoft/Boot` thus never loading linux, when selecting the drive directly from boot menu
- `/boot/efi/EFI/BOOT` will be checked second (if ever)
- To enforce usage of `/boot/efi/EFI/BOOT` required for Linux, a temporary solution would be renaming `/boot/efi/EFI/Microsoft/Boot` to `/boot/efi/EFI/Microsoft/NOT-Boot`

## Sources



