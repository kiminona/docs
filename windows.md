## powershell

- ### powershell profile location
```
C:\Users\[user]\Documents\WindowsPowerShell\profile.ps1
```
- ### get environment variables
```powershell
ls $Env
```
- ### get single environment variable
```powershell
$Env:Path
```
- ### Saving Changes to Environment Variables
```powershell
Add-Content -Path $Profile.CurrentUserAllHosts -Value '$Env:Path = $Env:Path + ";C:\Temp"'
```
- ### Get events from a specific event log with an Instance ID and Source value
```powershell
Get-EventLog -LogName System -EntryType Information -InstanceID 2147489653,2147489654 -Source EventLog
```
- ### Get all errors in an event log that occurred during a specific time frame
```powershell
PS C:\> $May31 = Get-Date 5/31/08
PS C:\> $July1 = Get-Date 7/01/08
PS C:\> Get-EventLog -Log "Windows PowerShell" -EntryType Error -After $May31 -before $July1
```
- ### unix xargs
```powershell
fd -e ext | ForEach-Object { rg -i word $_ }
```
