# Debian is not booting due to problems with grub
Windows 11 can occasionally break grub. Or the user mistakenly deletes the boot entry "debian" in BIOS setting. Or other stupid things happen

## Issue
- Debian 12 with grub
- Does not boot due to `/boot/efi/EFI/debian/` being broken
- E.g. selection in BIOS missing, not working, or bootlooping

### Solution
- Prepare a Debian usb stick (netinst sufficient), and boot in UEFI mode, no network needed
- Select `Advanced options...` &rarr; `...Rescue mode`
- Stick with defaults
  - `Select a language` &rarr; `English - English`
  - `Select your location` &rarr; `United States`
  - `Configure the keyboard` &rarr; `American English`
  - `Configure the network`
    - `Primary network interface` &rarr; `select any adapter (not WIFI if possible)`
    - `Network autoconfiguration failed` &rarr; `Continue`
    - `Network configuration method` &rarr; `Do not configure the network at this time`
    - `Hostname:` &rarr; `debian`
  - `Configure the clock`
- `Enter rescue mode`
  - `Passphrase for /dev/<encrypted partition>` &rarr; `Continue` (this shall pop up automatically)
  - `Device to use as root file system:` &rarr; `/dev/debian-volume-group-encyrpted/root`
  - `Mount separate /boot partition?` &rarr; `Yes`
  - `Mount separate /boot/efi partition?` &rarr; `Yes`
  - `Rescue operations` &rarr; `Reinstall GRUB boot loader` 
  - `Device for boot loader installation:` &rarr; `___leave_it_blank___` &rarr; `Continue` (which is effectively running `sudo grub-install`)
  - `Reboot the system`

## References
- [Grub reparieren](https://wiki.debianforum.de/Grub_reparieren#Wiederherstellung_bei_klassischer_Partitionierung_2)
