# Issue with fonts showing up as rectangles with random symbols inside
Wrong characters showing up in different browsers (Chrome, Chromium, Firefox).
Happening in the tab description and on the actual page.

# Solution
```bash
sudo apt install fonts-recommended
# Noto font families for Traditional Chinese, Simplified Chinese, Japanese and Korean
sudo apt install fonts-noto-cjk
# stuff by Microsoft "Microsoft True Type Core Fonts for the Web" in Debian 'contrib'
sudo apt install ttf-mscorefonts-installer
# maybe only this last one required???
sudo apt install fonts-noto
```

# References
- [Fonts - Debian Wiki](https://wiki.debian.org/Fonts)
- [Package: fonts-noto-cjk](https://packages.debian.org/sid/fonts-noto-cjk)
- [Package: ttf-mscorefonts-installer](https://packages.debian.org/bookworm/ttf-mscorefonts-installer)
- [Package: fonts-noto](https://unix.stackexchange.com/questions/570390/mozilla-wont-show-special-characters-such-as-chinese-korean-japanese-etc)
