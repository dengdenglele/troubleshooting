# Issue
- Platform: Debian based operating systems
- An upgrade runs out of space on `/boot`
- `/boot` partition cannot be easily enlarged on the fly without breaking the system
- `sudo apt autoremove` is not effective

# Solution
- untested:
```bash
sudo vi /etc/initramfs-tools/initramfs.conf
# look for COMPRESS=<something else> and set it to COMPORESS=xz
sudo update-initramfs -u
sudo reboot
```
- tested:
```bash
# identify available kernels
ls -la /boot
# -d for delete, -k for specific kernel version
sudo update-initramfs -d -k 6.8.0-48-generic
```

# References
- [XZ, GZIP, LZ4 and ZSTD: Which Format is Best of compression for SFS?](https://forum.puppylinux.com/viewtopic.php?t=8375)
- [zstd compression algorithm and the dethroned old king xz](https://sysdfree.wordpress.com/2020/01/04/293/)  
