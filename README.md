# X260 | oc0.8.6 | macOS 12.6.3
This is an iteration of [SuhailSherief's](https://github.com/SuhailSherief/ThinkPad-x260-macOS-OpenCore) already excellent OC configuration for the X260. I have added only minor changes for now, but as I add and configure for my own needs I will steadily stray from their configuration. Massive credit goes to them, if my config doesn't work for you try theirs.

**System Specifications**

| Spec | Config |
|--|--|
| CPU | i5-6300U |
| iGPU | Intel HD 520 |
| RAM | 8GB DDR4-2133 |
| SSD | SanDisk 256GB |
| Wi-Fi | Intel AC8260 |
| OC Ver | 0.8.6 |
| macOS | 12.6.4 (Monterey) |

**BIOS Settings**

-   `Security -> Security Chip`:  **False**

-   `Memory Protection -> Execution Prevention`:  **True**
-   `Virtualization -> Intel Virtualization Technology`:  **True**
-   `Virtualization -> Vt-Directed IO`:  **False**
-   `Internal Device Access -> Bottom Cover Tamper Detection`: **False**
-   `Anti-Theft -> Computrace -> Current Setting`:  **False**
-   `Secure Boot -> Secure Boot`:  **False**
-   `UEFI/Legacy Boot`:  **UEFI**
-   `CSM Support`:  **False**

**What's Working**

- Display `Hardware-accelerated graphics`
- Trackpad `All 3 HW Buttons and TrackPoint`
- Keyboard Backlight `Same behavior as on Windows/Linux`
- Audio `Integrated and HDMI`
- HDMI Output 
- Ethernet 
- Wi-Fi `With AirportItwlm v2.2.0 Alpha, was having issues with v2.1.0`
- iServices `With SMBIOS, I use MacBookPro 13,1, note that this will limit you to Monterey`
- Power Management
- Battery `LPM, Percentage`
- Sleep/Wake/Shutdown `Some Bluetooth issues with S3 sleep`

**Not working/Issues**

-  Experienced some kernel panics due to mbuf issues with AirportItlwm, tried using Itlwm with HeliPort but tried AirportItlwm v2.2.0 and seems to have resolved issues, will check back and try squash bugs

- SD Card Reader `Need to enable kexts`
- Bluetooth has some issues after S3 sleep, causing a "drive hash mismatch" error and refusing to work until you restart. You can try `sudo purge` or restarting the service but the permanent fix is to find your Bluetooth Address in `Apple Menu (While holding Alt) -> System Info -> Hardware -> Bluetooth` then append `export BT_DEVICE_ADDRESS="ma:ca:dd:re:ss:he:re"` to `/etc/zshenv`. This appears to have fixed it for me.

**ToDo**

- Enable SD Reader

- Update to latest OC
- Test new AirportItlwm and squash bugs
- Test support for Ventura and allow upgrade `Need to change SMBIOS`
