# GNOME goes to sleep after entering username and password in credentials
After login into GNOME, system immediately goes into sleep mode

## Issue
- Ubuntu 22.04 on Thinkpad L14 Gen 5 with external peripherals
- Right after login screen on gdm
  
Get diagnostics:
```bash
journalctl -eu systemd-logind
```

Output:
```bash
Jul 01 12:45:43 outback systemd[1]: Started User Login Management.
Jul 01 12:45:52 outback systemd-logind[1309]: New session c1 of user gdm.
Jul 01 12:46:13 outback systemd-logind[1309]: New session 2 of user cata0000.
Jul 01 12:46:14 outback systemd-logind[1309]: Suspending...
Jul 01 12:46:20 outback systemd-logind[1309]: Operation 'sleep' finished.
Jul 01 12:46:26 outback systemd-logind[1309]: Session c1 logged out. Waiting for processes to exit.
Jul 01 12:46:26 outback systemd-logind[1309]: Removed session c1.
Jul 01 12:47:42 outback systemd-logind[1309]: Session 2 logged out. Waiting for processes to exit.
Jul 01 12:47:43 outback systemd-logind[1309]: Suspending...
Jul 01 12:47:43 outback systemd[1]: Stopping User Login Management...
Jul 01 12:47:43 outback systemd-logind[1309]: Removed session 2.
Jul 01 12:47:43 outback systemd[1]: systemd-logind.service: Deactivated successfully.
Jul 01 12:47:43 outback systemd[1]: Stopped User Login Management.
Jul 01 12:47:43 outback systemd[1]: systemd-logind.service: Consumed 1.405s CPU time.
```


### Solution
- Create a new directory for drop-in files
- Create a drop-in file instead of adjusting `/etc/systemd/logind.conf`
  
```bash
sudo mkdir /etc/systemd/logind.conf.d
cat <<EOF | sudo tee /etc/systemd/logind.conf.d/handlelidswitch.conf
[Login]
HandleLidSwitch=ignore
EOF
```

- Check logs
```bash
journalctl -u systemd-logind
```

## References
- [Chapter 19. Here Documents](https://tldp.org/LDP/abs/html/here-docs.html)
- [Reddit](https://www.reddit.com/r/Proxmox/comments/kxdjrc/i_am_running_proxmox_on_a_thinkpad_laptop_how_can/)
