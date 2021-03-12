# Windows 9.5

## Step by Step Guide to Amerlioration

### 1. Open PowerShell (Admin) in the root of `C:` Drive and clone this repository. 

```powershell
git clone --recursive https://github.com/gamerhat18/windows-9.5 .
```

### 2. Have a Windows Installation Media plugged on your system. You can do this by either: 

 - Mounting a Windows 10 ISO file by right clicking on it and selecting `Mount`
 - Plugging in a Windows 10 USB Stick

Then, note down the drive letter of that Windows Installation Media (for eg. `G:\` or `H:\`)

### 3. Run `amelioration-first.bat` and select `Option 1` to run Pre-Amelioration script.

Then type the Drive letter that you got from `Step 2`. If the drive letter is `G:\`, then type `G:`, and so on.

### 4. Now boot into Linux (Live USB works fine too). Linux Mint/Pop OS, Ubuntu recommended.

 - Open up a terminal in the Windows Partition. 
 - Run `amelioration-second.sh` via bash and hit enter a bunch of times when asked a question, to go with the default options, as they work just fine.

```bash
bash amelirate-second.sh
```

### 5. Finally, boot back into Windows  

Open PowerShell (Admin), and run `amelioration-first.bat` again, but select `Option 2` to run Post-Amelioration script.

This will finish the Amerlioration Process, and you can then reboot to see the changes.



## How to Update Windows after Amelioration?

### 1. Do SSU (Service Stack) Update first and reboot
https://www.catalog.update.microsoft.com/Search.aspx?q=Servicing%20Stack%20Update%20Windows%2010

### 2. Then do comulative update last and reboot
https://www.catalog.update.microsoft.com/Search.aspx?q=Cumulative%20Update%20Windows%2010

> Make sure you download the Same MONTH and Architecture (x64)

### Steps to Extract and Install

```
C:\> expand -F:* <.msu file> <dest>
dism /online /add-package /packagepath=C:\Windows10.0-EXTRACTED-x64.cab
```

### Reboot between each one then run

```
dism /online /Cleanup-Image /StartComponentCleanup
```
