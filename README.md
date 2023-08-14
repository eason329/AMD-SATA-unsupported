# AMD-SATA-unsupported

Language: [ **English** | [繁體中文](README-ZH.md) ]

This kernel extension injects `AMD FCH SATA Controller` in AHCI mode, which is never supported by macOS. 

**This kext is intended to work on AMD system (especially AMD laptop), and does nothing in Intel system other than wasting your time!**

# macOS Compatibility

Known working: 11 Big Sur - 14 Sonoma

May work but not tested: 10.15 Catalina

* For `macOS 10.15 (Catalina)` and below, `AMD-SATA-unsupported.kext` is recommended
* For `macOS 11 (Big Sur)` and above, `CtlnaAMDAHCIPort.kext` is recommended.
  * However, you should first try `AMD-SATA-unsupported.kext` first as it is an injector kext and does not load extra executable. If you encounter kernel panic or other problem in DiskUtility, then try `CtlnaAMDAHCIPort.kext`.

`AMD-SATA-unsupported.kext` makes use of the IOClass `AppleIntelPchSeriesAHCI`, which was already removed by Apple since Big Sur. While this issue is mostly cosmetic, some users may encountered with problems such as `Couldn't alloc class "AppleIntelPchSeriesAHCI"` error, or hard drives not being detected in Disk Utility.

# Installation

**DO NOT use both kext at the same time!** Test the kext one by one and choose the most suitable one for you!

* Download the kext ZIP you want to use
* Unzip the kext
* Put the kext into OC/Kexts (or CLOVER/kexts/others) in your EFI folder
* Add the kext in config.plist

And you are done. Boot to macOS and test if the kext works.

# FAQ

## My disk is still not detected in DiskUtility
1. Open devmgmt.msc / Search 'Device Manager' in Windows
2. Expand "IDE ATA/ATAPI controllers" and open "Standard AHCI SATA controller"
3. Go to the Details tab and select Hardware IDs from the dropdown menu.
4. In the box underneath, you will find a string starting with PCI\VEN_####&DEV_$$$$.
5. Open the kext's Info.plist file with ProperTree and go to the AMD-FCH-AHCI section under IOKitPersonalities.
6. Open the sub-section called `IONameMatch`. Then add a new child under it. Set the type to String and set the value to `pci####,$$$$`.
7. Save the file and reboot
8. It should work now!


# Test Reports

This kext is tested on `macOS 11 (Big Sur)` and `macOS 12 (Monterey)` installed in a AMD laptop (Lenovo IdeaPad C340-14API) with SATA controller and works like a charm. Other versions may work but not tested.

# Credit

* Apple for macOS
* [Fabio1971](https://www.insanelymac.com/forum/profile/651049-fabio1971/) from insanelymac.com created the original AHCIPortInjector.kext
* [iFIRE and amdTnator](https://www.insanelymac.com/forum/topic/280681-amd-sata-controller/) from insanelymac.com gave me the idea
* RehabMan for providing SATA-unsupported.kext
* dortania for providing CtlnaAHCIPort.kext

# Disclaimer

* The author has no responsibility if your device bricked after you installed this kext. 
* The author has zero knowledge of programming kext, they may not able to answer your question or fix any bugs.
