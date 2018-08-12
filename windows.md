## powershell

- ### get environment variables
```
ls $Env
```
- ### get single environment variable
```
$Env:Path
```
- Saving Changes to Environment Variables
```
Add-Content -Path $Profile.CurrentUserAllHosts -Value '$Env:Path = $Env:Path + ";C:\Temp"'
```
