# AMDAHCIPortInjector

The kext expands the original [AHCIPortInjector.kext](https://www.insanelymac.com/forum/files/file/436-ahciportinjectorkext/). This kext can now injects `AMD FCH SATA Controller` in AHCI mode, which is never supported by macOS.

# Installation

* Download the repo as ZIP
* Unzip the kext
* Put the kext into OC/Kexts (or CLOVER/kexts/others) in your EFI folder
  * Make sure **NOT** to add AHCIPortInjector.kext as they are duplicated
* Add the kext in config.plist

And you are done. Boot to macOS and test if the text works.

# FAQ

soonTM

# Credit

* Apple for macOS
* [Fabio1971](https://www.insanelymac.com/forum/profile/651049-fabio1971/) from insanelymac.com created the original AHCIPortInjector.kext
* [iFIRE and amdTnator](https://www.insanelymac.com/forum/topic/280681-amd-sata-controller/) from insanelymac.com gave me the idea
