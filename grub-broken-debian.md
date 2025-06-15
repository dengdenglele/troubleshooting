# This is a template, describe shortly
Windows 11 can occasionally break grub. Or the user mistakenly deletes the boot entry "debian" in BIOS setting. Or other stupid things happen

## Issue
- Debian 12 with grub
- Does not boot due to `/boot/efi/EFI/debian/` being broken
- E.g. selection in BIOS missing, not working, or bootlooping

### Solution
- Prepare a Debian usb stick (netinst sufficient), and boot in UEFI mode, no network needed
- Select `Advanced options...` &rarr; `...Rescue mode`
- Stick with defaults
  - `Select a language`
  - `Select your location`
  - `Configure the keyboard`
  - `Configure the network` &rarr; `Do not configure the network at this time` &rarr; `Hostname: debian`
  - `Configure the clock`
- `Enter rescue mode`
  - will autodetect encrypted volume &rarr; decrypt it
  - `Device to use as root file system:` &rarr; `/dev/<name of the volume group>/root`
  - `Mount separate /boot partition?` &rarr; `Yes`
  - `Mount separate /boot/efi partition?` &rarr; `Yes`
  - `Rescue operation` &rarr; `Reinstall GRUB boot loader` (which is effectively running `sudo grub-install`)
  - `Device for boot loader installation:` &rarr; `___leave_it_blank___` &rarr; `Continue` (compare reference!)
  - `Reboot the system`

## References
- [Grub reparieren](https://wiki.debianforum.de/Grub_reparieren#Wiederherstellung_bei_klassischer_Partitionierung_2)
