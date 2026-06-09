Q1: Get the commands from the PSReadLine module.

A:

Get-Command -Module PSReadLine

#Initially used:
#Help PSReadLine

#Observed that Help PSReadLine displayed the cmdlets associated with the PSReadLine module

#Experimented with Get-Command and discovered that:
#Get-Command -Module PSReadLine directly retrieves commands belonging to the specified module

#Observed that both commands produced similar results in this case

#Learned that:
#Help is useful for discovering information about modules, cmdlets, and help topics
#Get-Command is specifically designed to retrieve commands

#Identified the PSReadLine module cmdlets:
#Get-PSReadLineKeyHandler
#Get-PSReadLineOption
#Remove-PSReadLineKeyHandler
#Set-PSReadLineKeyHandler
#Set-PSReadLineOption

#Reinforced Chapter 12 concepts:
#Command discovery
#Module filtering
#Retrieving specific command sets from a module

#Conclusion:
#Get-Command -Module PSReadLine is the most direct solution because it specifically retrieves commands contained within the PSReadLine module.

Q2: Get the commands using the verb Get from the PSReadLine module.

A:

Get-Command -Module PSReadLine |
Where-Object { $_.Verb -eq "Get" }

#Started by retrieving commands from the PSReadLine module using:
#Get-Command -Module PSReadLine

#Used Get-Member to inspect the properties available on the returned CmdletInfo objects

#Identified several useful properties including:
#Name
#Verb
#ModuleName
#Source

#Initially experimented with filtering on incorrect properties such as Module

#Observed that the Verb property contained values such as:
#Get
#Set
#Remove

#Used Where-Object to filter the command objects based on the Verb property

#Used the comparison operator -eq to return only commands whose Verb property was equal to "Get"

#Resulting commands:
#Get-PSReadLineKeyHandler
#Get-PSReadLineOption

#Learned that:
#Get-Command returns command objects, not just command names
#Where-Object filters objects based on property values
#The Verb property can be used to categorize PowerShell commands

#Reinforced Chapter 12 concepts:
#Object filtering
#Comparison operators
#Using object properties to narrow results
#Inspecting objects with Get-Member before filtering

Q3: Display all files under /usr/bin that are larger than 5 MB.

A:

Get-ChildItem "C:\Program Files" -File |
Where-Object { $_.Length -gt 5MB }

#Initially experimented with Get-Content, but observed that PowerShell returned errors indicating that directories cannot be read as file content

#Learned that Get-Content reads the contents of files, while Get-ChildItem retrieves filesystem objects

#Experimented with filtering on the Name property using:
#$_.Name -gt 5MB

#Observed that the command returned unexpected results because Name is a string property and does not represent file size

#Reviewed object properties and recalled from Chapter 11 that file objects contain a Length property

#Learned that the Length property stores the size of a file in bytes

#Used the comparison operator -gt to identify files larger than 5 MB

#Used the built-in PowerShell size constant:
#5MB

#Learned that:
#$_.Length refers to the Length property of the current file object being processed
#Where-Object filters objects based on property values
#The object type being filtered determines which properties are available

#Observed that running the command without the -File parameter returned primarily directory objects, which do not contain meaningful file size information

#Used the -File parameter to limit the results to file objects only

#Reinforced Chapter 12 concepts:
#Object filtering
#Comparison operators
#Using properties within Where-Object
#Understanding the role of $_ as the current object in the pipeline

#Conclusion:
#The correct solution filters file objects based on their Length property and returns only files larger than 5 MB.

Q4: Find all modules on the PowerShell Gallery that start with PS and have an author name that starts with Microsoft.

A:

Find-Module PS* |
Select-Object Name, Author |
Where-Object { $_.Author -like "Microsoft*" }

#Used Find-Module to search the online PowerShell Gallery repository

#Learned that Find-Module searches available modules in the PowerShell Gallery rather than modules already installed on the local system

#Initially experimented with:
#Get-Module -ListAvailable -Name PS*

#Observed that Get-Module searches locally installed modules and does not query the PowerShell Gallery

#Used Select-Object to display only the Name and Author properties

#Used Get-Member and property inspection techniques from earlier chapters to identify available module properties

#Used Where-Object to filter the returned module objects

#Used the Author property to identify modules published by Microsoft

#Used the -like comparison operator with a wildcard:

#"Microsoft*"

#To return authors whose names begin with "Microsoft"

#Observed matching modules such as:
#PSDSCResources
#PSScriptAnalyzer
#PSReadLine
#PSRule.Rules.Azure
#PSDesiredStateConfiguration

#Learned that:
#Find-Module returns module objects
#Where-Object filters objects based on property values
#The -like operator performs wildcard matching
#The * wildcard represents any number of characters

#Reinforced Chapter 12 concepts:
#Object filtering
#Property-based filtering
#Comparison operators
#Wildcard matching
#Using $_ to reference the current object in a pipeline

#Conclusion:
#The command successfully identified PowerShell Gallery modules whose names begin with PS and whose authors begin with Microsoft.

Q5: Get the files in the current directory where the LastWriteTime is within the last week.

A:

Get-ChildItem "C:\Users\deanschauer" |
Where-Object { $_.LastWriteTime -gt (Get-Date).AddDays(-7) } |
Select-Object Name, LastWriteTime

#Started by using Get-ChildItem to retrieve filesystem objects from the current directory

#Used Select-Object Name, LastWriteTime to inspect the available LastWriteTime values before attempting to filter the results

#Reviewed the lab hint:
#(Get-Date).AddDays(-7)

#Learned that:
#Get-Date returns the current date and time
#AddDays(-7) generates the date and time from one week ago

#Initially attempted to compare LastWriteTime to properties such as:
#$_.AddDays
#and other object properties

#Observed that the comparison date needed to be generated separately using:
#(Get-Date).AddDays(-7)

#Used Where-Object to filter the filesystem objects

#Used the comparison operator -gt to keep only objects whose LastWriteTime was greater than the date from seven days ago

#Learned that:
#$_.LastWriteTime refers to the LastWriteTime property of the current filesystem object
#Where-Object evaluates each object individually as it moves through the pipeline

#Observed that filtering should occur before Select-Object so that only matching objects are passed to the display stage

#Reinforced Chapter 12 concepts:
#Object filtering
#Date comparisons
#Comparison operators
#Using properties inside Where-Object
#Understanding $_ as the current object in the pipeline

#Conclusion:
#The command successfully returned files and folders whose LastWriteTime was within the last seven days.

Q6: Display a list of all processes running with either the name pwsh or the name bash.

A:

Get-Process |
Where-Object {
$*.ProcessName -eq "pwsh" -or
$*.ProcessName -eq "bash"
}

#Used Get-Process to retrieve process objects from the local system

#Initially experimented with placing the -or operator outside of the Where-Object script block

#Observed that PowerShell attempted to interpret -or as a parameter rather than a logical operator

#Learned that logical operators such as:
#-or
#-and

#Must be placed inside the Where-Object script block as part of a single logical expression

#Used the ProcessName property of each process object to identify matching processes

#Used the comparison operator -eq to perform exact string comparisons

#Used the logical -or operator to keep processes whose names were either:
#pwsh
#bash

#Observed that only pwsh processes were returned because no bash processes were running at the time of testing

#Learned that:
#$_.ProcessName refers to the ProcessName property of the current process object being evaluated
#Where-Object evaluates the entire logical expression for each object that moves through the pipeline

#Reinforced Chapter 12 concepts:
#Object filtering
#Comparison operators
#Logical operators
#Using $_ inside Where-Object
#Building compound filter conditions

#Conclusion:
#The command successfully filters process objects and returns only processes whose names match either pwsh or bash.
