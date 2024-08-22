# Issue
- Platform: Debian 12 on Thinkpad T14 Gen 2 11th Gen Intel CPU
- Does not record with hardware encoding
- Crash after start recording
# Solution
- OBS Studio crashes immediatley after settings were changed
- Simple restart the application and hit recording again

# Other solutions
- Try out "intel-media-va-driver-non-free" package [debian wiki](https://wiki.debian.org/HardwareVideoAcceleration), [obsproject forum](https://obsproject.com/forum/threads/how-to-use-qsv-vaapi-on-linux-mint.137329/)
- Verify hardware acceleration in "intel_gpu_top" command (from "intel-gpu-tools" package)
