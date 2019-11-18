# PowerShell Conveniences

### Switches

`-NoExit` - Keeps ps window open; useful for debugging macros that are ran when a document is open

### Commands

Gets installed software, version, and install date.
```PowerShell
Get-ItemProperty HKLM:\Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall\* | Select-Object DisplayName, DisplayVersion, InstallDate
```

Web requests (if one doesnt work, try the other). PowerUp!
```PowerShell
Invoke-WebRequest -Uri <target uri> -Method Get -Outfile <whatevs>.ps1 #IWR
powershell IEX(New-Object Net.Webclient).downloadString("<target uri>") #Invoke-Expression
```

"which" nix-style output.
```powershell
Get-Command <your command> | Select-Object -ExpandProperty Definition
```

"grep"-like with x number of lines before or after.
```powershell
<whatever cmd> | Select-String -Pattern "whatevs" -Context 2,4
```
