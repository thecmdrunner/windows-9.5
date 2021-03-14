# Windows 9.5

## Part 1: Modifying the Vanilla Windows 10 ISO

### 1. Download the Official Windows 10 ISO from Microsoft

 - Head over to [Microsoft Software Downloads](https://www.microsoft.com/en-in/software-download/windows10ISO)
 - Select English International and 64-Bit Version (Other languages might not work flawlessly) 

### 2. Download [MSMG Toolkit](https://msmgtoolkit.in/download.html)

  - Unzip the contents into a new `MSMG` folder on your desktop.
  - Extract the contents of the Windows ISO to the `Desktop\MSMG\DVD\` 

### TODO

## Part 2: Guide to Amerlioration

Now that you have installed Windows 10 from the ISO that you just made, it's time to ameliorate it and make the experience as good as (or even better than) **Windows 7**

### 1. Open PowerShell and clone this repository in the `C:\` directory. 

```powershell
git clone --recursive https://github.com/gamerhat18/windows-9.5 .
```

### 2. Mount a Windows Installation Media on your system by either: 

 - Mounting a Windows 10 ISO file by right clicking on it and selecting `Mount`
 - Plugging in a Windows 10 USB Stick

Then, note down the drive letter of that Windows Installation Media (for eg. `G:\` or `H:\` Drive)

### 3. Run `AME-Win.bat` as Administrator and select `Option 1` to run Pre-Amelioration script.

Then type the Drive letter that you got from `Step 2`. If the drive letter is `G:\`, then type `G:`, and so on.


### 4. Now boot into Linux (Live USB works fine too). Linux Mint/Pop OS/Ubuntu recommended.

> **NOTE: You must shutdown Windows by typing `shutdown /s /f /t 0` in Powershell/CMD instead of Shutting Down normally, to avoid Dirty NTFS Drive Problems.**
- Open up a terminal in the Windows Partition. 
- Run `amelioration-second.sh` with root privileges and hit enter a bunch of times when asked a question, to go with the ideal default options.

```bash
sudo sh AME-Linux.sh
```

### 5. Finally, boot back into Windows  

Run `AME-Win.bat` as Administrator again and select `Option 2` to run Post-Amelioration script.

This will finish the Amerlioration Process, and you can then reboot to see the changes.


## How to Update Windows after Amelioration?

### 1. Do SSU (Service Stack) Update first and reboot

Go To: [Microsoft Service Stack Update Catalog](https://www.catalog.update.microsoft.com/Search.aspx?q=Servicing%20Stack%20Update%20Windows%2010)

### 2. Then do comulative update last and reboot

Go To: [Microsoft Cumulative Update Catalog](https://www.catalog.update.microsoft.com/Search.aspx?q=Cumulative%20Update%20Windows%2010)

> Make sure you download the Same MONTH and Architecture (x64) for both of them

### Then Extract and Install

```
C:\> expand -F:* <.msu file> <dest>
dism /online /add-package /packagepath=C:\Windows10.0-EXTRACTED-x64.cab
```

### Reboot between each one then run

```
dism /online /Cleanup-Image /StartComponentCleanup
```
