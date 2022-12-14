# WSL


# 5. WSL installation:

## 5.1. Enable WSL, Default install subsyetm, update wsl

** If you are a VDI user, and have a Docker VDI requested, this needs to be done by installing WSL trough the software center.

  - Windows Subsystem for Linux is enabled
      - Open PowerShell as Administrator `(Start menu > PowerShell > right-click > Run as Administrator)` and enter this command:
        ```
        dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
        wsl --install
        ```
  
  - Reboot system

  On start u see that Ubuntu is installing, when asked for a username, u can close that terminal screen.

  Now, open your powershell and run: `wsl --help`

  See if the option for `--import` is listed between the commands. If there is no option for it please do the next steps, else move on to the next chapter.
        
    - Download & install the Linux kernel update package --> https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi
        
## 5.2. Create Base Folders:
Open powershell

```
mkdir C:\Users\$env:UserName\WSL
mkdir C:\Users\$env:UserName\WSL\rootdata
mkdir C:\Users\$env:UserName\WSL\rootdata\.kube
```

### 5.2.1. Existing Kubectl config
If you have a Existing Kubectl config, then place this in C:/Users/C00000/WSL/rootdata/.kube/config

```
cp C:\Users\$env:UserName\.kube\config C:\Users\$env:UserName\WSL\rootdata\.kube
```

## 5.3. Download the Linux-package.

Choose your distro. Simply use one of these URLs:
- https://wsldownload.azureedge.net/Ubuntu_2004.2020.424.0_x64.appx

### 5.3.1. Extract (7zip)
- extract the appx file, and copy/move the install.tar.gz, and move this to WSL folder (C:\Users\C00000\WSL)

## 5.4. Install

This way of installng your WSL has the option to generate/create multible instances.

in powershell (as administrator)
```
cd C:\Users\$env:UserName\WSL
wsl --set-default-version 1
wsl --import Ubuntu-2004-00 .\Ubuntu-2004-00 .\install.tar.gz
```

### 5.4.1. Multible instances
if you want 10 instances :D
```
$count=0
0..10 |% {
    $count = (1+ $count).ToString('00')
    
    Write-Host $count
    wsl --import Ubuntu-2004-$count .\Ubuntu-2004-$count .\install.tar.gz
}
```

## 5.5. Run
```
wsl -d Ubuntu-2004-00
```

# 9. Tooling
For each time u want to start and stop u can also use:
- https://github.com/bostrot/wsl2-distro-manager

Advice is not to use the other function that the tooling provides.

