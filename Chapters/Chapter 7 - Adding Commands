Q1: Browser the powershell gallery. Find a module or two that you think sounds interesting and install it.

A:

Find-Module PSScriptAnalyzer
Install-Module PSScriptAnalyzer

Find-Module ThreadJob
Install-Module ThreadJob

#Used Find-Module to search the PowerShell Gallery for available modules
#Installed the PSScriptAnalyzer module for PowerShell script analysis and best-practice checking
#Installed the ThreadJob module for lightweight background job/thread management

#Observed the PSGallery repository trust warning during installation
#Learned that PowerShell prompts for confirmation when installing from repositories that are not yet marked as trusted

#Learned that PowerShell modules extend functionality by adding additional cmdlets, automation features, and administrative tooling

Q2: Browse the available commands for the module you just downloaded

A:

Get-Command -Module PSScriptAnalyzer

#Used Get-Command with the -Module parameter to display cmdlets included in the PSScriptAnalyzer module

#Observed the following cmdlets included with the module:
#Get-ScriptAnalyzerRule
#Invoke-Formatter
#Invoke-ScriptAnalyzer

Help Get-ScriptAnalyzerRule -Full

#Reviewed detailed help documentation for the Get-ScriptAnalyzerRule cmdlet
#Explored cmdlet syntax, parameters, descriptions, and rule management functionality

Get-Command -Module ThreadJob

#Used Get-Command with the -Module parameter to display cmdlets included in the ThreadJob module

#Observed the Start-ThreadJob cmdlet included with the module

Help Start-ThreadJob -Full

#Reviewed detailed help documentation for the Start-ThreadJob cmdlet
#Learned that ThreadJob provides lightweight background job functionality using threads instead of separate PowerShell processes

#Learned that PowerShell modules act as containers/packages that provide additional cmdlets and functionality
#Learned that module cmdlets should be explored individually using Get-Command and Help rather than searching the module name directly

Q3: Use the commands from section 7.2 to find and install (if needed) the latest version module by Microsoft for working with archives to contain the command "Compress-Archive"

A:

#Tested the Compress-Archive cmdlet by compressing a text file into a ZIP archive
#Observed that Compress-Archive was already available as a built-in PowerShell cmdlet/module on the system
#Connected built-in module functionality with the chapter discussion about installing additional modules from PowerShell Gallery

Q4: Import the module you just installed

A:

Import-Module Microsoft.PowerShell.Archive

#Used Import-Module to manually load the archive-related PowerShell module

#Observed that Compress-Archive was already available on the system before manual import
#Learned that some modules are built into PowerShell and may automatically import when their cmdlets are used

#Connected the relationship between modules and cmdlets:
#Module -> Microsoft.PowerShell.Archive
#Cmdlet -> Compress-Archive

#Learned that modules can either be manually imported with Import-Module or automatically imported by PowerShell when associated cmdlets are called

Q5: Create a test folder for the next step with 10 files in it and name it ~\TestFolder

A:

New-Item -Path "C:\Users\deanr\OneDrive\Documents\PowerShell" -ItemType Directory -Name TestFolder

1..10 | ForEach-Object {
    New-Item -Path "C:\Users\deanr\OneDrive\Documents\PowerShell\TestFolder" -Name "Test$_.txt" -ItemType File
}

#Created a TestFolder directory using New-Item
#Used the PowerShell range operator (1..10) to generate a sequence of numbers

#Used ForEach-Object to iterate through each number in the range
#Used the current pipeline object ($_ ) to dynamically generate filenames:
#Test1.txt through Test10.txt

#Learned that PowerShell pipelines can automate repetitive administrative tasks
#Combined ranges, pipelines, and object iteration to create multiple files with a single command sequence

#Initially considered manually creating all 10 files individually
#Researched and explored automation-oriented approaches to better understand PowerShell pipeline behavior and repeated task automation

Q6:

A:

Compress-Archive -Path "C:\Users\deanr\OneDrive\Documents\PowerShell\TestFolder" -DestinationPath "C:\Users\deanr\OneDrive\Documents\PowerShell\TestFolder.zip" -Force -Verbose

#Used Compress-Archive to compress the TestFolder directory into a ZIP archive
#Specified the source folder using the -Path parameter
#Specified the ZIP archive output location using -DestinationPath

#Used -Force to allow overwriting an existing archive if necessary
#Used -Verbose to display detailed operational output during the compression process

#Observed PowerShell reporting archive preparation and file additions during execution
#Learned that Compress-Archive can package directories and files into ZIP archives directly through PowerShell

Q7: Expand the archive to TestFolder2

A:

Expand-Archive -Path "C:\Users\deanr\OneDrive\Documents\PowerShell\TestFolder.zip" -DestinationPath "C:\Users\deanr\OneDrive\Documents\PowerShell\TestFolder2"

#Used Expand-Archive to extract the contents of the ZIP archive into a new directory
#Specified the source archive using the -Path parameter
#Specified the extraction destination using -DestinationPath

#Recognized the complementary relationship between Compress-Archive and Expand-Archive cmdlets
#Applied PowerShell naming conventions and parameter patterns without requiring additional help documentation

#Verified that the contents of TestFolder.zip were successfully extracted into the TestFolder2 directory

Q8: Use Compare-Object and Select-Object -ExpandProperty Name to compare just the names of the files in the folders to verify you have the same files.

A:

Compare-Object `
    -ReferenceObject (
        Get-ChildItem "C:\Users\deanr\OneDrive\Documents\PowerShell\TestFolder" |
        Select-Object -ExpandProperty Name
    ) `
    -DifferenceObject (
        Get-ChildItem "C:\Users\deanr\OneDrive\Documents\PowerShell\TestFolder2\TestFolder" |
        Select-Object -ExpandProperty Name
    ) `
    -IncludeEqual

#Used Get-ChildItem to retrieve files from both directories
#Used Select-Object -ExpandProperty Name to compare only the filenames rather than full file objects

#Used Compare-Object to compare the file name lists between the original and extracted folders
#Used -IncludeEqual to display matching file names using the == side indicator

#Initially attempted to compare folder paths directly rather than the file objects within the folders
#Learned that Compare-Object compares the objects provided to it, not the folder contents automatically

#Initially misunderstood how Select-Object receives pipeline input
#Learned that Get-ChildItem must provide file objects before Select-Object can expand the Name property

#Observed that the extracted archive created a nested TestFolder directory inside TestFolder2
#Adjusted the comparison path to:
#"C:\Users\deanr\OneDrive\Documents\PowerShell\TestFolder2\TestFolder"

#Observed that Compare-Object returns no output when no differences exist unless -IncludeEqual is specified

#Noticed PowerShell sorted filenames alphabetically rather than numerically:
#Test1.txt
#Test10.txt
#Test2.txt
#...
#Learned that string sorting behavior differs from human numeric ordering
