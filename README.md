# Windows-Terminal

## comandos a utilizar, desde powershell con privilegios de administrador

- choco install oh-my-posh
- Install-Module oh-my-posh -Scope CurrentUser 
- PowerShellGet\Install-Module posh-git -Scope CurrentUser -Force
- Install-Module PowerShellGet -AllowClobber -Force
- Install-Module PSReadLine -AllowClobber -Force 
- Install-Module -AllowClobber Get-ChildItemColor
- choco install lsd
- choco install git
- choco install microsoft-windows-terminal

## profile.ps1

```bash
Import-Module posh-git
Import-Module oh-my-posh
Set-PoshPrompt -Theme agnoster

#hde username@domain
$defaultUsers = 'Kidcode1'

#helper function to change directory to development workspace
#function cws { Set-Location C:\Kidcode1\projects}

Import-Module Get-ChildItemColor

Import-Module PSReadLine

# Shows navigable menu of all options when hitting Tab
Set-PSReadLineKeyHandler -Key Tab -Function MenuComplete

# Autocompleteion for Arrow keys
Set-PSReadLineOption -HistorySearchCursorMovesToEnd
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadLineKeyHandler -Key DownArrow -Function HistorySearchForward

Set-PSReadLineOption -ShowToolTips
Set-PSReadLineOption -PredictionSource History

#Set the color for Prediction (auto-suggestion)

#set theme for oh-my-posh
#Set-PoshPrompt -Theme powerlevel10k_rainbow
#Set-PSReadlineOption -Colors @{Prediction = 'DarkGreen' }
Set-PSReadLineOption -Colors @{InlinePrediction = "$([char]0x1b)[36;7;238m]"}

if (-Not (Test-Path Variable:Psise)){
    #only run this in the console and not in the ISE
    Import-Module Get-ChildItemColor

    Set-Alias l Get-ChildItem -option AllScope
    Set-Alias ls Get-ChildItemColorFormatWide -option AllScope
}
```

## para el archivo settings.json

estas lineas debera ser copiado y pegado despues de la palabra profiles, respetando las llaves.

```json

    "profiles": 
    {
        "defaults": 
        {
            "acrylicOpacity": 0.3,
            "font": 
            {
                "face": "Hack Nerd Font Mono"
            }
        },
        "list": 
        [
            {
                "acrylicOpacity": 0.9,
                "backgroundImage": "c:/terminal/terminal.jpg",
                "backgroundImageOpacity": 0.2,
                "commandline": "powershell.exe -NoLogo",
                "font": 
                {
                    "face": "Hack Nerd Font Mono"
                },
                "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
                "hidden": false,
                "name": "Windows PowerShell",
                "useAcrylic": true
            },
            {
                "acrylicOpacity": 0.39999999999999997,
                "backgroundImage": "c:/terminal/terminal.jpg",
                "backgroundImageOpacity": 0.2,
                "commandline": "cmd.exe",
                "font": 
                {
                    "face": "Hack Nerd Font Mono"
                },
                "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
                "hidden": false,
                "name": "S\u00edmbolo del sistema",
                "useAcrylic": true
            },
            
```

**Kidcode1
