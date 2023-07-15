# AMD-SATA-unsupported

語言: [ [English](README.md) | **繁體中文** ]

此內核延伸會把將未被 macOS 所支援的 `AMD FCH SATA Controller`（AHCI 模式）注入到該作業系統。 

**此內核延伸只會在 AMD 系統（尤其是 AMD 筆記型電腦）工作，在 Intel 系統上除了浪費您的時間之外沒有任何作用！**

# macOS 相容性

* `macOS 10.15 (Catalina)` 和更舊系統，建議使用 `AMD-SATA-unsupported.kext`
* `macOS 11 (Big Sur)` 和更新系統，建議使用 `CtlnaAMDAHCIPort.kext`
  * 但是，您應首先試用 `AMD-SATA-unsupported.kext`，因為它不會載入額外的內核插件。如果您遇到內核錯誤或在磁碟工具程式中出現其他問題，請嘗試使用 `CtlnaAMDAHCIPort.kext`。

`AMD-SATA-unsupported.kext` 使用一個名為 `AppleIntelPchSeriesAHCI` 的 IOClass 類別，但蘋果已經在 Big Sur 中移除了這個類別。雖然這個問題大多不會影響作業系統工作，部分用戶可能會遇到諸如 `Couldn't alloc class "AppleIntelPchSeriesAHCI"` 錯誤，或無法在磁碟工具程式找到磁碟等等的問題。

# 安裝方式

**不要同時使用這兩個 kext！** 請逐一測試，然後選擇最適合自己的 kext！

* 下載您想要使用的 kext ZIP
* 解壓 kext
* 將 kext 放入 EFI 資料夾中的 OC/Kexts（或 CLOVER/kexts/others）
* 在 config.plist 中加入 kext

你就完成了。 啟動 macOS 來測試 kext 是否正常工作。

# FAQ

soonTM

# 測試報告

此 kext 在安裝在帶有 SATA 控制器的 AMD 筆記本電腦 (Lenovo IdeaPad C340-14API) 上的 `macOS 11 (Big Sur)` 和 `macOS 12 (Monterey)` 上進行了測試，並且能正常工作。其他版本可能可以工作，但未經測試。

# 鳴謝

* Apple for macOS
* 來自 insanelymac.com 的 [Fabio1971](https://www.insanelymac.com/forum/profile/651049-fabio1971/) 建立原版 AHCIPortInjector.kext
* 來自 insanelymac.com 的 [iFIRE and amdTnator](https://www.insanelymac.com/forum/topic/280681-amd-sata-controller/) 給作者靈感製作這個 kext
* dortania 分發的 CtlnaAHCIPort.kext

# 聲明

* 如果您安裝此 kext 後設備變磚或導致您的 AppleID 遭停用，作者不承擔任何責任。
* 作者對 kext 的編程知識基本為零，他們可能無法回答您的問題或修復錯誤。
