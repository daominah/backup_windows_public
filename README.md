# Set up a Windows 10 computer

This GitHub repository is a clone of
[GoogleDrive\usual_app_Windows](https://drive.google.com/drive/folders/1ArpNEL_9r1cseumE0etTTNJBLCixth8i?usp=sharing),
but only includes links to download app installers, not the installers
(except for some installers are hard to download).

Both this GitHub repository and the mentioned GoogleDrive directory are PUBLIC,
do NOT put sensitive information here.

Be aware of Google Drive does not have ".gitignore" equivalent feature and
GitHub blocks files larger than 100 MiB (need [Git Large File Storage](git_for_windows_download.txt)).

Git and Google Drive do not work well together.
Git can have pull error, but push is fine, can ignore the error.

The full list of files in this dir is [ls_this_dir.txt](ls_this_dir.txt),
was created by `ls -lh --time-style=+%Y-%m-%d > ls_this_dir.txt`

### Create boot USB

Use Microsoft Windows 10 Installation Media Creation Tool:

* File `GoogleDrive\usual_app_Windows\MediaCreationTool22H2_Windows10.exe`, OR
* Download from [Microsoft](https://www.microsoft.com/en-us/software-download/windows10).

Do NOT choose the tool output as an `.iso` file,
Microsoft does not provide a way to verify if the file correctly downloaded.

### Install and update Windows

After installed, **set a computer name**, example `tungdtWindowsGram17z90q`, restart.
If you do not set, the computer name is a random string, e.g. DESKTOP-9ULQBFD.

Go to `Start: Check for updates` to **update Windows** to the latest version
(because the Windows downloaded from Installation Media Creation Tool can be very old).
After that, you should `Advanced options: Pause updates: max 35 days`.

### Optimize for performance

#### Power plan

* Show `Ultimate Performance` power plan with Windows PowerShell:

  ```powershell
  powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61
  ```

* Start Menu: Change a power plan: Ultimate Performance.

#### Disable visual effects

Windows crap effects significantly slow down the computer. For example:

* Linux Mint runs Master Duel 3840x2160 and watches YouTube 1080p at the same time smoothly.
* Windows 10 runs Master Duel 2560x1440 and watches YouTube 480p makes the video freeze.

So you should disable visual effects:

* Start Menu: View advanced system settings: Performance: Settings:
  Adjust for best performance (all visual effects are unchecked):
  check `Smooth edges of screen fonts`: Apply.
* Start Menu: Themes: Color:
  - unchecked `Transparency effects`
  - check show color on `Title bars and window borders` (default does not show border)

Windows sometimes screw up the settings when updating.

### Install usual apps

(If the computer will be used as a server, you should install apps as admin user)

Check the computer directory `GoogleDrive\usual_app_Windows` to see if the
installers are here, so you don't need to download them from the internet.

Install important apps first, example: Git, Firefox, 7z, ... You can come back
to this step later (there are a lot of apps).

### Pirate (optional)

TLDR: open `Windows PowerShell` as admin:

```
irm https://massgrave.dev/get | iex
```

Reference: [github.com/massgravel/Microsoft-Activation](https://github.com/massgravel/Microsoft-Activation-Scripts)

### Enable administrator account (optional)

* open `cmd.exe` as admin:

  ```
  net user administrator /active:yes
  ```

* Set administrator account password (default admin does not have a password):

  `Sign-in options`: `Password`: `Add`

* Disable default `Quick Edit` in `cmd` app (to prevent accidentally freeze it).

* Permanently disable Windows update :
  [TODO, maybe this is not possible](https://superuser.com/questions/946957/stopping-all-automatic-updates-windows-10).

### Remote control (optional)

##### TeamViewer

* Download the [TeamViewer installer](TeamViewer_download.txt).
* If you want to install TeamViewer for a server, you want to be able to remote
  control the server from your personal computer anytime but not vice versa,
  choose install options `Custom installation with unattended access support`,
  `Personal use`, `Show advanced settings`. Untick `Keep me signed in option`
  before login. Then set options:
  - `General`: `Start TeamViewer with Windows` (default: enable).
  - `Security`: `Grant you easy access`.
  - `Advanced`: `Check for new version`: `Never`.
  - `Advanced`: `Disable TeamViewer shutdown`.
  - Log out.

##### Windows Remote desktop RDP

* `Remote desktop settings`: `Enable remote desktop`.
* `Computer management`: `Local Users and Groups`: `Groups`: `Remote Desktop Users`: `Add`.

### Open listening ports (optional)

* `Windows Defender Firewall`: `Advanced Settings`: `Inbound rules`: `New rule` ([reference](https://vinasupport.com/huong-dan-mo-cong-open-port-tren-windows-server/)).

* Then go to network modem setting (usually at 192.168.1.1) to map ports.  
  If Firefox gets error `SSL_ERROR_UNSUPPORTED_VERSION`: `security.tls.version.enable-deprecated`. ([reference](https://stackoverflow.com/a/71411721/4097963))  
  Modem settings are usually named DHCP, static IP, Forward Rules.

* Useful commands:

  ```
  :: look for value of Ethernet adapter Physical address
  ipconfig /all
  
  :: refresh after config static IP
  ipconfig /release
  ipconfig /renew
  ```

### Hide This PC entries in Windows Explorer

Set or New String Value `ThisPCPolicy` to `Hide` in the following registry key:

| Entry      | Registry key                                                                                                                                         |
|------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| Documents  | Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{f42ee2d3-909f-4907-8871-4c22fc0bf756}\PropertyBag |
| Downloads  | Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{7d83ee9b-2244-4e70-b1f5-5393042af1e4}\PropertyBag |
| Music      | Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{a0c69a99-21c8-4671-8703-7934162fcf1d}\PropertyBag |
| Picture    | Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{0ddd015d-b06c-45d5-8c4c-f59713854639}\PropertyBag |
| Videos     | Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{35286a68-3c57-41a1-bbb1-0eae73d76c95}\PropertyBag |
| 3D Objects | Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FolderDescriptions\{31C0DD25-9439-4F12-BF41-7FF4EDA38722}\PropertyBag |

Reference: <https://superuser.com/questions/1470599/hide-3d-objects-from-this-pc>
