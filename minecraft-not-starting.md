# Minecraft Launcher does not start on Fedora
Starting minecraft via terminal only leads to two "OK" and then stops silently

## Issue
- Platform: Fedora 43 with sway
- Application: minecraft-launcher as AppImage from official minecraft page
- After entering `~/minecraft-launcher` in terminal
- The last line in the logs in `~/.minecraft/launcher_log*.txt` complains about `[Warning: 2025-12-13 14:42:20.011482834: d8ydZGMwgmk=: PlatformLinux.cpp(280)] Failed to get framebuffer config`


### Solution
```bash
__GLX_VENDOR_LIBRARY_NAME=mesa ~/minecraft-launcher
```

## References
- [Reddit post](https://www.reddit.com/r/Fedora/comments/1p9flhs/curseforge_not_operating_properly/)
