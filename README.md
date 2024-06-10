# HP-EliteBook-830-G5-OpenCore
check my score [Geekbench](https://browser.geekbench.com/v6/cpu/5901430)

<img src="/Picture/Sonoma.png"  width="1000">
<img src="/Picture/Sonoma 2.png"  width="1000">
<img src="/Picture/Sonoma 3.png"  width="1000">

<summary><strong>My Hardware 💻</strong></summary>
</br>

| Category                | Specification                                                                                                        |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------|
| Model                   | [HP EliteBook 830 G5](https://support.hp.com/vn-en/document/c05898590)                                               |
| Processor               | 8th Gen Intel® Core™ i5-8350U processor, 4 Cores / 8 Threads, 1.7 GHz / 3.6 GHz (Base / Max Turbo), 6 MB Cache       |
| Graphics (Integrated)   | Intel® UHD Graphics 620                                                                                              |
| 13.3" Display           | 120Hz Full HD, 16:9 aspect ratio                                                                                     |
| Storage                 | 512 GB SSD M.2 NVMe WDC PC SN720 SDAPNTW-512G-1006 best choice for hackintosh)                                       |
| Memory                  | 16 GB Samsung dual-channel DDR4-2400 MHz (8 GB x 2)                                                                  |                     
| WLAN + Bluetooth        | Broadcom BCM94360CS2 with adapter (best choice for hackintosh)                                                       |

<summary><strong>Bios Setting</strong></summary>
</br>

```diff

Advanced

->   Boot Options
Startup Menu Delay(sec.) = 0
Fast Boot uncheck
CD-ROM Boot uncheck
USB Storage Boot checked
Network (PXE) Boot unchecked
Power On When AC Detected unchecked
Power On When Lid is Opened unchecked
Prompt on Battery Errors checked
Prompt of Memory Size Change checked
Prompt on Fixed Storage Change checked
Audio Alerts During Boot checked
NumLock on at Boot unchecked
UEFI Boot Order checked
Legacy Boot Order checked

->   Secure Boot Configuration
Configure Legacy Support and Secure Boot = Legacy Support Disable and Secure Boot Disable

->   System Options
Turbo Boost checked
Hyperthreading checked
Multi-processor checked
Virtualization Technology (VTx) check
Virtualization Technology for Directed I/O (VTd) checked
Swap Fn and Ctrl (keys) unchecked
Launch Hotkeys without Fn Keypress unchecked
Enable Turbo Boost on DC unchecked

->  Built-In Device Options
Embedded LAN Controller checked
Wake on LAN disabled
Video memory size 64MB
Audio Device checked
Integrated Microphone checked
Internal Speakers checked
Lock Wireless Button unchecked
Wireless Network Device (WLAN) checked
Bluetooth checked
LAN / WLAN Auto Switching disabled
Fan Always on while on AC Power unchecked
Fan Quiet Mode unchecked
Backlit keyboard timeout 10 sec.
Integrated Camera checked
Fingerprint Device unchecked
NFC checked

->   Port Options
Left USB Ports checked
Right USB Ports checked
Right USB Port1 checked
Right USB Port2 checked
USB Charging Port Function checked
Disable Charging Port in sleep/off if battery below (%) = 10
Media Card Reader checked
Smart Card unchecked
Smart Card Power Savings unchecked
M2 SSD1 checked
SATA1 checked
Restrict USB Devices = Allow all USB Devices

->   Option ROM Launch Policy
Configure Option ROM Launch Policy = All Legacy

->   Power Management Options
Runtime Power Management checked
Extended Idle Power States checked
Deep Sleep checked
Wake when Lid is Opened checked
Wake on USB unchecked
Power Control unchecked

```


<summary><strong>How to install macOS</strong></summary>
</br>

1. [Create an installation media](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/#making-the-installer)
1. Download the this EFI and copy it into the ESP partiton
1. Boot from the USB installer (press `F12` to choose boot volume) and [start the installation process](https://dortania.github.io/OpenCore-Install-Guide/installation/installation-process.html#booting-the-opencore-usb)

<summary><strong>Enable Apple Services</strong></summary>
</br>

1. Run the following script in Terminal

```bash
git clone https://github.com/corpnewt/GenSMBIOS && cd GenSMBIOS && chmod +x GenSMBIOS.command && ./GenSMBIOS.command
```

2. Type `3` to Generate SMBIOS, then press ENTER
3. Type `MacBookPro15,4 5`, then press ENTER. Leave this Terminal window open.
4. Open `/EFI/OC/Config.plist` with any editor and navigate to `PlatformInfo -> Generic`
5. Add the script's last result to `MLB, SystemSerialNumber and SystemUUID`

```diff

<key>Generic</key>
<array>
  </dict>
    <key>AdviseFeatures</key>
    <false/>
    <key>MLB</key>
    <string>*****************</string>
    <key>MaxBIOSVersion</key>
    <false/>
    <key>ProcessorType</key>
    <integer>0</integer>
    <key>ROM</key>
    <data>lVhEd021</data>
    <key>SpoofVendor</key>
    <true/>
    <key>SystemMemoryStatus</key>
    <string>Auto</string>
    <key>SystemProductName</key>
    <string>MacBookPro15,4</string>
    <key>SystemSerialNumber</key>
    <string>*************</string>
    <key>SystemUUID</key>
    <string>*******-****-****-****-************</string>
  </dict>
</array>

```

<summary><strong>What's not working ⚠️</strong></summary>
</br>

- [ ] Fingerprint
- [ ] WWAN
- [ ] IR Camera
- [ ] Fan speed monitor
- [ ] You talk to me
