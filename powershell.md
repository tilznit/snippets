# PowerShell Conveniences

### Switches

`-NoExit` - Keeps ps window open; useful for debugging macros that are ran when a document is open

### Commands

```PowerShell
Get-ItemProperty HKLM:\Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall\* | Select-Object DisplayName, DisplayVersion, InstallDate
```
Gets installed software, version, and install date.
