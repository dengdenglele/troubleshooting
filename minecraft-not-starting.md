# Minecraft Launcher does not start on Fedora
Starting minecraft via terminal only leads to two "OK" and then stops silently

## Issue 1
- Platform: Fedora 43 with sway
- Application: minecraft-launcher as AppImage from official minecraft page
- After entering `~/minecraft-launcher` in terminal

### Solution
```bash
__GLX_VENDOR_LIBRARY_NAME=mesa ~/minecraft-launcher
```

## References
- [Reddit post](https://www.reddit.com/r/Fedora/comments/1p9flhs/curseforge_not_operating_properly/)
