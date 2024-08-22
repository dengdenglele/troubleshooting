# Issue
- Platform: Debian 12 (minimal installation) on Thinkpad T14 Gen 2 11th Gen Intel CPU
  - Change encoder setting: Settings > Output > Recording > Encoder > FFmpeg VAAPI H.264
  - OBS crashes when clicking "Start Recording"
    
# Solution
- Restart the application and "Start Recording" without entering the Settings menu

# Other solutions
- Try out "intel-media-va-driver-non-free" package [debian wiki](https://wiki.debian.org/HardwareVideoAcceleration), [obsproject forum](https://obsproject.com/forum/threads/how-to-use-qsv-vaapi-on-linux-mint.137329/)
- Verify hardware acceleration in "intel_gpu_top" command (from "intel-gpu-tools" package)
- Platform: Debian 12 (with default settings: "Debian desktop environment", "GNOME" and "standard system utilities") on Thinkpad T14 Gen 2 11th Gen Intel CPU
  - Change encoder setting: Settings > Output > Recording > Encoder > FFmpeg VAAPI H.264
  - OBS does not crash when clicking "Start Recording"
