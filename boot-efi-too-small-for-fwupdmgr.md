# Issue with space on /boot/efi
When running `fwupdgmr update`, the program might complain about disk space at `/boot/efi` being too small
    
# Solution
- Check the disk size of `/boot/efi` with `ncdu` while being root with `sudo su`, identify large directories
- E.g. move the directory `/boot/efi/EFI/Microsoft` to `/boot/Microsoft` temporary

# Restore original structure and check disk space on /boot/efi
- Be sure to move back directories to their original places
- After running `fwupdmgr update` successfully, `boot/efi` might occupy more space, because inside `/boot/efi/EFI/debian/fw` is a large `fwupd-xxxxxx.cap` file, which was needed for update the firmware
