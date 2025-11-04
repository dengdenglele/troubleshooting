# Issue with small font size in tty
Using screens with high pixel density can lead to very small font size in tty

# Solution
```bash
sudo dpkg-reconfigure console-setup

# Select "UTF-8"
# Select "Latin1 and Latin5..."
# Select "Terminus"
# Select "16x32 (framebuffer only)"
```

Note: 
- Current settings are stored `/etc/default/console-setup`
- Editing this file does not affect the tty size, must be changed via command above
