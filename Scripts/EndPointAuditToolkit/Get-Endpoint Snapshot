# This script provides a basic snapshot of the current endpoint.

# Display script title in terminal
Write-Host "=== Endpoint Snapshot Script ===" -ForegroundColor Cyan
Write-Host ""

#Gather computer information (Name, OS, OSVersion, Username)
Write-Host "`n=== Computer Info ===" -ForegroundColor Cyan
Get-ComputerInfo -Property CsDNSHostName, CsUserName, OsName, OsVersion | Format-List 

#Gather the current powershell version
Write-Host "`n=== PowerShell Version ===" -ForegroundColor Cyan
$PSVersionTable.PSVersion |
Format-List 

#Get the last time that the device booted
Write-Host "`n=== Last Boot Time ===" -ForegroundColor Cyan
Get-Uptime -Since

#Get a list of local administrators
Write-Host "`n=== Local Administrators ===" -ForegroundColor Cyan
Get-LocalGroupMember -Group Administrators |
    Select-Object Name, ObjectClass, PrincipalSource |
    Format-Table -AutoSize

#Get the top 5 processes currently consuming memory
Write-Host "`n=== Top 5 processes by memory ===" -ForegroundColor Cyan
Get-Process |
    Sort-Object -Property WorkingSet64 -Descending |
    Select-Object -First 5 -Property `
        @{Name = 'ProcessName'; Expression = { $_.Name } },
        @{Name = 'MemoryMB'; Expression = { [math]::Round($_.WorkingSet64 / 1MB, 2) } } |
    Format-Table |
    Out-Host

#Count the number of services currently running on the computer
Write-Host "`n=== Service Count ===" -ForegroundColor Cyan
    (Get-Service | Where-Object { $_.Status -eq "Running" }).Count |
    Out-Host

#Get the disk space available
Write-Host "`n=== Available Disk Space ===" -ForegroundColor Cyan
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType = 3" |
    Select-Object DeviceID, VolumeName,
        @{Name = 'SizeGB'; Expression = { [math]::Round($_.Size / 1GB, 2) } },
        @{Name = 'FreeGB'; Expression = { [math]::Round($_.FreeSpace / 1GB, 2) } } |
    Format-Table -AutoSize |
    Out-Host
