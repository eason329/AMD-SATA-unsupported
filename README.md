# AMDAHCIPort

The kext expands the original [AHCIPortInjector.kext](https://www.insanelymac.com/forum/files/file/436-ahciportinjectorkext/). This kext can now injects `AMD FCH SATA Controller` in AHCI mode, which is never supported by macOS.

Note: The `CtlnaAMDAHCIPort.kext`, which is based on `CtlnaAHCIPort.kext`, has not been tested and does not work (Remind that this controller is not Intel).

# macOS Compatibility

`macOS 11 (Big Sur)` and `macOS 12 (Monterey)`. Other version may work but not tested.

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
