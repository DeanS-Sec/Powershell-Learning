Q1: Create a new directory called labs

A:

New-Item "C:\Users\deanr\OneDrive\Documents\PowerShell" -ItemType Directory -Name Labs

#Used the New-Item cmdlet to create a new directory
#Specified the parent directory path for the new folder location
#Used -ItemType Directory to create a folder instead of a file
#Used -Name Labs to assign the folder name
#Verified successful directory creation through PowerShell output

Q2: Create a zero-length file named \Labs\Test.txt 

A:

New-Item "C:\Users\deanr\OneDrive\Documents\PowerShell\Labs\" -ItemType File -Name Test.txt

#Used the New-Item cmdlet to create a new file
#Specified the parent Labs directory path for the file location
#Used -ItemType File to create a file instead of a directory
#Used -Name Test.txt to assign the filename

#Verified the file was created successfully through PowerShell output
#Observed the Length property returned a value of 0, confirming the file contains no data

Q3: Is it possible to use Set-Item to change the contents of \Labs\Test.txt to -Testing? Do you get an error? If so, why?

A:

Set-Item "C:\Users\deanr\OneDrive\Documents\PowerShell\Labs\Test.txt" -Value TESTING

#Initial attempts using Set-Item resulted in provider operation errors
#Discovered the FileSystem provider does not support using Set-Item to modify file contents directly

#Explored alternative content-related cmdlets through the help system
#Tested Add-Content to successfully write data into the file

Add-Content -LiteralPath "C:\Users\deanr\OneDrive\Documents\PowerShell\Labs\Test.txt" -Value "TESTING"

#Used Add-Content to append text into the file successfully
#Verified the file contents could be modified using content-management cmdlets instead of Set-Item

Q4: Using the environment provider, display the value of the system environment using variable PATH

A: 

Get-Item -Path Env:Path

#Used the Environment provider through the Env: drive
#Retrieved the PATH environment variable using Get-Item
#Observed that environment variables can be accessed similarly to filesystem items through PowerShell providers

#Learned that the PATH variable stores directories the operating system searches when commands or executables are run from the terminal

Q5: Use help to determine what the differences are between the -Filter, -Include, and -Exclude paramters of Get-ChildItem

A:

Okay so filter is used to to narrow down a specific function/command. For example, when searching for commands, maybe you want to filter out ones that would be for writing or erasing if you were looking for commands to sort. 
-Include/Exclude would for sorting information that you do or do not want. Whether it is including/excluding specific files types in a search
