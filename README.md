# kubenPS
Powershell scripts for Kuben skole

Her vil vi gå gjennom kommandoer og oppsett for Hyper-V på Windows 10 i første omgang. 
Husk at du må være i PowerShell som administrator (eller i VS Code eller Terminal) 

Installere PowerShell v. 7 ved hjelp av Winget
Winget Install Microsoft.PowerShell
Installere Windows Terminal ved hjelp av Winget
Singet Install Microsoft.WindowsTerminal

Mer info og nedlasting av Windows Terminal
https://learn.microsoft.com/en-us/windows/terminal/

Mer info og nedlasting av PowerShell 7
https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.3

Jeg har prøvvd å lage en form av struktur, slik at du kan velge området du er interessert i. Om du har noe kunnskap om PS, så kan du starte hvor du vil. Om du starter fra 0, så gå til ExploringPS først.

# Utforske PowerShell 

## Formater for cmdlet
` "Verb-Noun" `

## Help system,
### Legg til bryteren -ShowWindow for å åpne i egen søkbart windu.
```
Get-Help    
Update-Help
Get-Help about*
Get-Help about_modules -ShowWindow
```

## Command explore
```
Get-Verb | Measure-Object
Get-Command | Measure-Object
```
## Get, Set, New, Connect, Exit, 
### Explore modules
```
Get-Module -All
Get-Module -Name Microsoft.PowerShell.Utility
Get-Command -Module NetTCPIP 
Get-Command -Module Hyper-V
Get-Command -Module Microsoft.PowerShell.Security
Get-Command -Module ActiveDirectory -Verb get
```
```
get-help *vm*
Get-Command -Module Hyper-V
get-help *switch*
Get-Command -Module NetworkSwitchManager
```

# FileHandling, her har jeg satt inn variabelen '$HOME', denne peker alltid til din hjemmefolder i windows.

` Get-ChildItem -Path $HOME\Downloads `
` New-Item -Name 'Sharing' -ItemType Directory -Path $HOME\Documents  `

# Klienthåndtering
```
Get-Command -Module Microsoft.PowerShell.Management
(Get-ComputerInfo).HyperVisorPresent
Get-command -module Microsoft.PowerShell.Security
```
```
Set-Clipboard(Get-Process)
Get-Clipboard
Get-ComputerInfo
(Get-ComputerInfo).BiosFirmwareType
(Get-ComputerInfo).CsProcessors
$memgb = (Get-ComputerInfo).CsPhysicallyInstalledMemory
$memgb
```

# ServerManagement   
```
Get-Command -Module ServerManager
Get-Command -Module IISAdministration
Get-Command -Module grouppolicy

```

## Format to the right, select to the left
```
Get-Process vmmem |Select-Object name, cpu |Format-Table name, CPU #Right
Get-Process vmmem |Format-Table name, CPU |Select-Object name, cpu #Wrong
```

## Input in Powershell
```
Write-Output -InputObject 'Hello World!'
$name = Read-Host -Prompt "Please enter your name"
Write-Output "Congratulations $name! You have written your first code with PowerShell!"
Get-Help -Name Read-Host -Full
```

## Variabler i PowerShell 
### Legg til -Online på Get-Help så vil du få opp websiden med hjelp, ofte vil du finne videre informasjon der.
```
$_ 
$PSVersionTable
$
Get-Help about_Variables
Get-Help about_Environment_Variables
```

## Providers i PowerShell. Providers gir oss en måte å interagere med data som er lagret i Windows.
## Det være seg filsystemer, eller registeret. Kjør kommandoen under for å se alle tilgjengelige
```
Get-PSProvider
Get-PSProvider -PSProvider FileSystem
Get-PSDrive
Get-PSDrive -PSProvider Function
Get-Command -FullyQualifiedModule Microsoft.PowerShell.Management
Get-ChildItem -Path
```
