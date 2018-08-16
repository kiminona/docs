## powershell

- ### get environment variables
```
ls $Env
```
- ### get single environment variable
```
$Env:Path
```
- ### Saving Changes to Environment Variables
```
Add-Content -Path $Profile.CurrentUserAllHosts -Value '$Env:Path = $Env:Path + ";C:\Temp"'
```
- ### Get events from a specific event log with an Instance ID and Source value
```
Get-EventLog -LogName System -EntryType Information -InstanceID 2147489653 -Source  EventLog
Get-EventLog -LogName System -EntryType Information -InstanceID 2147489654 -Source  EventLog
```
