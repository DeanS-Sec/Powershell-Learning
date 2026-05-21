Q1: Display a list of running processes

A:
Get-Process

#Retrieves currently running processes on the local computer

Q2: Test the connection to google.com or bing.com without using an external command like ping

A:

Test-Connection

#Initial network-related searches
Help *network*
Get-Command *network*

#Explored Test-ADTNetworkConnection but encountered positional parameter errors
#Determined this was not the intended built-in PowerShell cmdlet

#Refined search using connection-related keywords
Help *connection*
Get-Command *connection*

#Discovered Test-Connection cmdlet for built-in connectivity testing

Q3: Display a list of all commands that are of the cmdlet type.

A:

Get-Command -CommandType Cmdlet

#Review Get-Command help and parameters
Help Get-Command

#Discovered the -CommandType parameter can filter commands by type

#Used -CommandType Cmdlet to display only PowerShell cmdlets

Q4: Display a list of all aliases.

A:

Get-Alias

#Review PowerShell alias help topics
Help about_aliases

#Discovered Get-Alias can display all currently defined aliases

Q5: Make a new alias, so you can run ntst to run netstat from a Powershell prompt.

A:

New-Alias -Name "ntst" -Value netstat

#Create a custom alias named ntst
#Mapped ntst to the netstat command

#Verified alias functionality by running:
#ntst

Q6: Display a list of processes that begin with the letter p. 

A:

Get-Process -Name "p*"

#Retrieves running processes from the local computer
#Uses the -Name parameter to filter process names
#Uses the wildcard p* to return processes beginning with the letter P

Q8:7 Make a new folder using the New-Item cmdlet with the name of MyFolder1. Repeat for MyFolder2

A:

New-Item -Path "C:\Users\deanr\OneDrive\Documents\PowerShell\MyFolder1" -ItemType "Directory"

New-Item -Path "C:\Users\deanr\OneDrive\Documents\PowerShell\MyFolder2" -ItemType "Directory"

#Used the New-Item cmdlet to create directories
#Specified the full directory path using -Path
#Used -ItemType "Directory" to create folders
#Created MyFolder1 and MyFolder2 successfully

Q8:Remove the folders from step 7 in a single command. 

A:

Remove-Item -Path "C:\Users\deanr\OneDrive\Documents\PowerShell\MyFolder1", "C:\Users\deanr\OneDrive\Documents\PowerShell\MyFolder2" -Force

#Used Remove-Item to delete both folders in a single command
#Passed multiple folder paths through the -Path parameter
#Used -Force after encountering access/read-only related errors

#Alternative wildcard approach explored:
#Remove-Item -Path "C:\Users\deanr\OneDrive\Documents\PowerShell\MyFolder*" -Force

#Learned that wildcard matching can target multiple folders sharing the same naming pattern

