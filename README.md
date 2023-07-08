 # AMD-SATA-unsupported

This kernel extension injects `AMD FCH SATA Controller` in AHCI mode, which is never supported by macOS. 

**This kext is intended to work on AMD system (especially AMD laptop), and does nothing in Intel system other than wasting the space!**

# macOS Compatibility

This kext is tested on `macOS 11 (Big Sur)` and `macOS 12 (Monterey)` installed in a AMD laptop (Lenovo IdeaPad C340-14API) with SATA controller and works like a charm. Not work on `macOS 13 (Ventura)` as the kext caused kernel panic. Other versions may work but not tested.

This kext makes use of the IOClass `AppleIntelPchSeriesAHCI`, which was already removed by Apple since Big Sur. While this issue is mostly cosmetic, some users may encountered with problems such as `Couldn't alloc class "AppleIntelPchSeriesAHCI"` error, or hard drives not being detected in Disk Utility.

If you going to install macOS 11 or newer, try `AMD-SATA-unsupported.kext` first. If the kext does not work, then try `CtlnaAMDAHCIPort.kext`, which is based on `CtlnaAHCIPort.kext`.

# Installation

* Download the kext ZIP you want to use
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
* dortania for providing CtlnaAHCIPort.kext
