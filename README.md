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
4. In the box underneath, you will find a string starting with PCI\VEN_1002&DEV_####.
5. Open the kext's Info.plist file with ProperTree and go to the AMD-FCH-AHCI section under IOKitPersonalities.
6. Open the sub-section called `IONameMatch`. Then add a new child under it. Set the type to String and set the value to `pci1002,####`.
7. Save the file and reboot
8. It should work now! You can even submit a PR here to help other people :D

## When I opened the Settings app, it crashed immediately
This problem is caused by "Volume hash mismatch" error. Apple has integrated "About this Mac" into Settings app since macOS 13. Therefore the error can actually crash the whole app. To fix this problem:
1. Open Automator app and click "Add"
2. Choose "Application" as workflow type and click "Choose"
3. Click "Utlilties", then drag "Run Shell Script" to the right of the screen
4. Type the following code: `echo " *Your account's password if set* " | sudo -S purge`
5. Save (to anywhere you won't delete)

You can now run the app on the location you just saved each time the problem occured. After that, the Settings app should be opened with no problem. However, if you want to run the app each time you log in:

6. Open Settings app and select "General" --> "Log In Items"
7. Click "+" and select the app you just created.

Make sure your account is administrator when running the script.


# Credit

* Apple for macOS
* [Fabio1971](https://www.insanelymac.com/forum/profile/651049-fabio1971/) from insanelymac.com created the original AHCIPortInjector.kext
* [iFIRE and amdTnator](https://www.insanelymac.com/forum/topic/280681-amd-sata-controller/) from insanelymac.com gave me the idea
* RehabMan for providing SATA-unsupported.kext
* dortania for providing CtlnaAHCIPort.kext

# Disclaimer

* The author has no responsibility if your device bricked after you installed this kext. 
* The author may not able to answer your question or fix bugs.
