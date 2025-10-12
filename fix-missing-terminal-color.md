# Remote machine accessed via SSH do not show color coding in terminal
When accessing a remote machine, it can happen that the terminal does not display color coding.

## Issue
- Fedora sway accessing a Debian server
- Fedora sway is using foot terminal
- Prompt is not colored
- Commands such as `ls` are not colored

### Solution
- Debian requires `xterm-color256` instead of `foot` for the `TERM` environment variable
  - Check with `echo $TERM` what is currently being used
  - It affects the color coding in `ls` etc.
- Edit the `~/.bashrc` to universally force color coding independent of host machine
```bash
# uncomment the following line, or add it manually
force_color_prompt=yes

# add at the end of the .bashrc
export TERM=xterm-256color
```

- As an alternative add those two lines in a separate file, e.g. `~/.bash_customized` and include it in `~/.bashrc`
