# AMD-SATA-unsupported

The kext expands the original [AHCIPortInjector.kext](https://www.insanelymac.com/forum/files/file/436-ahciportinjectorkext/). This kext can now injects `AMD FCH SATA Controller` in AHCI mode, which is never supported by macOS. **This kext is intended to work on AMD system (especially AMD laptop). Putting this in any Intel system will not work!**

Warning: The included `CtlnaAMDAHCIPort.kext`, which is based on `CtlnaAHCIPort.kext` **does not work** right now.

# macOS Compatibility

This kext is tested on `macOS 11 (Big Sur)` and `macOS 12 (Monterey)` installed in a AMD laptop (Lenovo IdeaPad C340-14API) with SATA controller and still usable. Other versions may work but not tested.

This kext relies on the IO class `AppleIntelPchSeriesAHCI`, which was already removed by Apple since Big Sur. While this issue is mostly cosmetic, some users may encountered with problems such as `Couldn't alloc class "AppleIntelPchSeriesAHCI"` error, or hard drives not being detected in Disk Utility.

# Installation

* Download the repo as ZIP
* Unzip the kext
* Put the kext into OC/Kexts (or CLOVER/kexts/others) in your EFI folder
* Add the kext in config.plist

And you are done. Boot to macOS and test if the kext works.

# FAQ

soonTM

# Credit

* Apple for macOS
* [Fabio1971](https://www.insanelymac.com/forum/profile/651049-fabio1971/) from insanelymac.com created the original AHCIPortInjector.kext
* [iFIRE and amdTnator](https://www.insanelymac.com/forum/topic/280681-amd-sata-controller/) from insanelymac.com gave me the idea
