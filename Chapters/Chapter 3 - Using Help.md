Chapter 3 Lab.
Q1: Update help and ensure it completes correctly, as well as save the help locally to your computer.

A: 
#Updates local powershell help files
Update-Help

#Saves downloadable help files locally
Save-Help -DestinationPath ".\HelpFiles"

Q2: Can you find any cmdlets capable of converting other cmdlets' output into HTML?

A: 
#Gather information regarding Html syntax
Help *Html*
#Confirm no other Html commands I missed
Get-Command *Html*

Q3: Are there any cmdlets that can redirect output into a file?

A: 
#Search for output-related cmdlets
Help *output*

#Found Write-Output, which sends objects to the pipeline

#Search for file-related cmdlets
Help *file*
#Discovered Out-File, which sends output to a file

Q4: How many cmdlets are available for working with processes?

A:
#Initial search only returned 2 process-related cmdlets
Help *get-process*

#Expanded search to all process-related commands
Help *process*

#Discovered 12 process-related cmdlets

Q5: What cmdlet might you use to set a powershell breakpoint?

A:
#Initial wildcard search for breakpoint-related help
Help *breakpoint*

#Found Set-PSBreakpoint cmdlet

#Alternative method to search for breakpoint-related commands
Get-Command *breakpoint*

Q6: You've learned that aliases are nicknames for cmdlets. What cmdlets are available to create, modify, export, or import aliases?

A:
#Search for alias-related help topics and cmdlets
Help *alias*

#Found alias management cmdlets:
#New-Alias
#Set-Alias
#Import-Alias
#Export-Alias
#Remove-Alias

#Alternative command discovery method
Get-Command *alias*

Q7: Is there a way to keep a transcript of everything you type in the shell, and save that transcript to a text file?

A:
#Initial search using plural returned no results
Help *transcripts*

#Successful transcript-related search
Help *transcript*

#Alternative command discovery method
Get-Command *transcript*

#Found transcript logging cmdlets:
#Start-Transcript
#Stop-Transcript

Q8: Getting all processes can be overwhelming. How can you get processes by the name of the process?

A:
#Review Get-Process syntax and parameters
Help Get-Process

#Discovered the -Name parameter can retrieve specific processes by name

#Example:
#Get-Process -Name explorer

Q9: Is there a way to tell Get-Process to tell you the user who started the process?

A:
#Review Get-Process syntax and parameters
Help Get-Process

#Discovered the -IncludeUserName parameter displays the user associated with a running process

#Example:
#Get-Process -Name chrome -IncludeUserName

Q10: Is there a way to run a command on a remote host?

A:
#Search for invoke-related help topics
Help *invoke*

#Alternative command discovery method
Get-Command *invoke*

#Found Invoke-Command cmdlet for running commands on local and remote computers

Q11: Examine the help file for the "Out-File" cmdlet. The files created by this cmdlet default to a width of how many characters? Is there a parameter that would enable you to change the width?

A:
80 characters. The -Width parameter can change it.

#Review full help for Out-File to find default behavior and parameter details
Help Out-File -Full

#Found that Out-File defaults to 80 characters wide
#Found that -Width can be used to change the output width

Q12: By default, Out-File overwrites any existing file that has the same filename as what you specify. Is there a parameter that would prevent the cmdlet from overwriting the existing file?

A:
-NoClobber prevents Out-File from overwriting an existing file.

#Review full help for Out-File parameter details
Help Out-File -Full

#Found that -NoClobber prevents overwriting existing files
#Found that Out-File overwrites files by default unless -NoClobber is specified

Q13: How could you see a list of all aliases defined in powershell

A:
#Retrieve all currently defined PowerShell aliases
Get-Alias

Q14: Using both an alias and abbreviated parameter names, what is the shortest command line you could type to retrieve a list of commands with the word process in the name?

A:
gcm *process

Q15: How many cmdlets are available that can deal with generic objects?

A:

10 cmdlets

#Search for object-related cmdlets and help topics
Help *object*

#Alternative command discovery method
Get-Command *object*

#Found 10 object-related cmdlets

Q16: This chapter has briefly mentioned arrays. What help topic could tell you more about them?

A:

about_Arrays

#Search for array-related help topics
Help *array*

#Open the arrays help topic in full detail
Help about_Arrays -Full


