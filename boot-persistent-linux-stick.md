# Make any external drive with fully installed Linux bootable
Linux distributions can be installed on USB thumb drives.
Data is persistent and thumb drive can be plugged into different host devices.

## Issue
- Some distros do not boot without issues or changes in BIOS/UEFI
- Problematic distros:
  - Debian
  - Kali

## Solution
- A full disk installation of Ubuntu on an external device creates an bootloader structure which can be used universally on any external device
- This bootloader structure can be copied to "problematic" distros and used after modifications
- It might be necessary to mount /boot/efi partition, otherwise /boot/efi directory stays empty

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

- The .EFI and .efi files in both BOOT/ and ubuntu/ are binary files and must not be changed or deleted!
- The name of the directory "ubuntu" can be changed into something else e.g. "kali" or "debian"
- Within **ubuntu/grub.cfg** the existing UUID must be changed to the UUID of the /boot partition of the other distro
  - Output: search.fs_uuid <insert-the-new-UUID-here> root    
  - Use "lsblk"
  - and "blkid"
- Open **ubuntu/BOOTX64.CSV** with VSCode
  - Output: shimx64.efi,Ubuntu,,This is the boot entry for ubuntu
  - It might be neccesary to copy BOOTX64.CSV somewhere else and adapt permissions before changes can be made
  - The boot entry (second field) for the BIOS can be changed, e.g. change "Ubuntu" to "Kali Linux"
  - The last field allows to writes a description
  - After changes were made, open BOOTX64.CSV with nano or vi and check and delete "strange" characters created by VSCode

## Sources

