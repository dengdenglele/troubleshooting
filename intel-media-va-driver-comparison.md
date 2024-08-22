# Comparison of intel-media-va-driver vs intel-media-va-driver-non-free comparison

NOTE: Only one intel-media-va-driver can exist at the same time, when installing the other one, the existing one will be automatically removed

Free driver, pre-installed with basic Debian 12 installation

```bash
sudo apt install intel-media-va-driver
vainfo | grep Enc > intel_free
cat intel_free
# Output
      VAProfileH264Main               :	VAEntrypointEncSliceLP
      VAProfileH264High               :	VAEntrypointEncSliceLP
      VAProfileJPEGBaseline           :	VAEntrypointEncPicture
      VAProfileH264ConstrainedBaseline:	VAEntrypointEncSliceLP
      VAProfileHEVCMain               :	VAEntrypointEncSliceLP
      VAProfileHEVCMain10             :	VAEntrypointEncSliceLP
      VAProfileHEVCMain444            :	VAEntrypointEncSliceLP
      VAProfileHEVCMain444_10         :	VAEntrypointEncSliceLP
      VAProfileHEVCSccMain            :	VAEntrypointEncSliceLP
      VAProfileHEVCSccMain10          :	VAEntrypointEncSliceLP
      VAProfileHEVCSccMain444         :	VAEntrypointEncSliceLP
      VAProfileHEVCSccMain444_10      :	VAEntrypointEncSliceLP
```

Non-free driver allows encoding of more media formats

```bash
sudo apt install intel-media-va-driver-non-free
vainfo | grep Enc > intel_non-free
cat intel_non-free
# Output
      VAProfileMPEG2Simple            :	VAEntrypointEncSlice
      VAProfileMPEG2Main              :	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointEncSliceLP
      VAProfileH264High               :	VAEntrypointEncSlice
      VAProfileH264High               :	VAEntrypointEncSliceLP
      VAProfileJPEGBaseline           :	VAEntrypointEncPicture
      VAProfileH264ConstrainedBaseline:	VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:	VAEntrypointEncSliceLP
      VAProfileHEVCMain               :	VAEntrypointEncSlice
      VAProfileHEVCMain               :	VAEntrypointEncSliceLP
      VAProfileHEVCMain10             :	VAEntrypointEncSlice
      VAProfileHEVCMain10             :	VAEntrypointEncSliceLP
      VAProfileHEVCMain12             :	VAEntrypointEncSlice
      VAProfileHEVCMain422_10         :	VAEntrypointEncSlice
      VAProfileHEVCMain422_12         :	VAEntrypointEncSlice
      VAProfileHEVCMain444            :	VAEntrypointEncSliceLP
      VAProfileHEVCMain444_10         :	VAEntrypointEncSliceLP
      VAProfileHEVCSccMain            :	VAEntrypointEncSliceLP
      VAProfileHEVCSccMain10          :	VAEntrypointEncSliceLP
      VAProfileHEVCSccMain444         :	VAEntrypointEncSliceLP
      VAProfileHEVCSccMain444_10      :	VAEntrypointEncSliceLP
```

Sources:
- [Debian Wiki](https://wiki.debian.org/HardwareVideoAcceleration)
