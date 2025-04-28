# ddterm and Forge Gnome extensions interaction and bugs
When both extensions are installed, they might interfere with each other

## Issue 1
- Any distro with GNOME and ddterm and Forge enabled
- Forge causes ddterm to jump around

### Solution
- Use Forge shortcut `Shift + Super + C` to disable tiling mode for ddterm
- If `Shift + Super + C` does not work, also try out `Ctrl + Alt + C`

## Issue 2
- Any distro with GNOME and ddterm and Forge enabled
- Forge causes ddterm window to shrink on the left and the right side, height stays the same

### Solution
- Limit the height to 80% max (it depends on the screen size, can be more or less depending on device)
- Either in preferences menu or with `Ctrl + Down`

## Issue 3
- Any distro with GNOME and Forge enabled
- Keybindings might interfere with default keybinding

### Solution
- Change "Hide window" shortcut to `Alt + Super + H`
- Change "Lock Screen" shortcut to `Alt + Super + L`

## References
- [Issue 1 on GitHub](https://github.com/forge-ext/forge/issues/387)
