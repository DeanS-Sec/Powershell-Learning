Q1: Create two similar, but different text files. Try comparing them by using Compare-Object. 

A:

New-Item -Name "Text1.txt" -ItemType "File" -Path "C:\Users\deanr\OneDrive\Documents\PowerShell" -Value "Coffee is essential"

New-Item -Name "Text2.txt" -ItemType "File" -Path "C:\Users\deanr\OneDrive\Documents\PowerShell" -Value "Water is essential"

#Created two separate text files with different text content
#Used the -Value parameter to write initial text into each file during creation

Compare-Object -ReferenceObject (Get-Content "C:\Users\deanr\OneDrive\Documents\PowerShell\Text1.txt") -DifferenceObject (Get-Content "C:\Users\deanr\OneDrive\Documents\PowerShell\Text2.txt")

#Used Get-Content to retrieve the contents of both text files
#Passed the file contents into Compare-Object for comparison
#Observed SideIndicator results showing which lines existed only in each file

#Learned that plain text files should use Get-Content rather than Import-Csv or Import-Clixml
#Learned that Compare-Object can compare objects and content provided through the pipeline

Q2: What happens if you run Get-Command | Export-CSV commands.CSV | Out-File from the console? Why does that happen?

A:

Get-Command | Export-CSV commands.csv | Out-File fromconsole.txt

#Tested pipeline behavior using Get-Command, Export-CSV, and Out-File
#Observed that Out-File generated errors related to missing or invalid path handling

#Determined that Export-CSV already consumes the pipeline objects and writes them directly into commands.csv
#Learned that Export-CSV functions as an output destination cmdlet rather than continuing meaningful object output down the pipeline

#Learned that chaining Out-File after Export-CSV does not work as expected because the pipeline data flow is interrupted by Export-CSV writing directly to a file

Q3: Apart from getting one or more jobs and pping them to Stop-Job, what other means does Stop-Job provide for you to specify the job or jobs you want to stop? Is it possible to stop a job without using Stop-Job at all?

A:

Yes. Stop-Job can target jobs directly by using parameters such as -Id, -InstanceId, -Name, or -State.

#Reviewed Stop-Job help and parameter options
Help Stop-Job

#Found that Stop-Job can identify jobs directly without requiring Get-Job pipeline input
#Learned that jobs can be stopped by specifying identifiers such as -Id, -InstanceId, -Name, or filtering by -State

Q4: What if you want to create a pipe-delimited file instead of a CSV file? You'd still use the Export-CSV command, but what parameters would you specify?

A: 

Export-Csv -Delimiter "|"

#Reviewed Export-Csv help and parameter information
Help Export-Csv -Full

#Discovered the -Delimiter parameter can change the separator character used during export
#Learned that the pipe symbol (|) must be placed inside quotation marks because PowerShell normally interprets | as the pipeline operator

#Learned that delimiters determine how exported data fields are separated
#Compared pipe-delimited exports with standard comma-delimited CSV formatting

Q5: How do you include the type information in the # comment line at the top of an exported CSV file?

A:

Export-Csv -NoTypeInformation

#Reviewed Export-Csv help and parameter details
Help Export-Csv -Parameter NoTypeInformation

#Discovered the -NoTypeInformation parameter suppresses the type metadata normally inserted at the top of exported CSV files

#Learned that PowerShell parameters can be researched individually using:
#Help <Cmdlet> -Parameter <ParameterName>

#Observed that parameter-specific help may provide metadata and syntax details, while additional research/examples may still be useful for deeper practical understanding

Q6: Export-Clixml and Export-CSV both modify the system because they can create and overwrite files. What parameter would prevent them from overwriting an existing file? What parameter would ask whether you were sure before proceeding to write the output file?

A:

-NoClobber
-WhatIf
-Confirm

#Reviewed Export-Clixml and Export-Csv parameter information
#Discovered -NoClobber prevents overwriting existing files
#Discovered -WhatIf simulates the operation without making changes
#Discovered -Confirm prompts the user for confirmation before proceeding

#Learned that these parameters are commonly used to add safety protections to PowerShell commands and automation workflows

Q7: The OS maintains several regional settings which include a default list separator. On US systems, that seperator is a comma. How can you tell Export-CSV to use the systems default separator rather than a comma?

A: 

Export-Csv -UseCulture

#Reviewed Export-Csv help and parameter information
Help Export-Csv -Full

#Discovered the -UseCulture parameter uses the operating system’s regional list separator instead of the default comma delimiter

#Learned that different operating systems and regional settings may use different delimiters such as commas or semicolons

#Connected the concept of delimiters with previous Export-Csv parameter exploration using -Delimiter
#Observed that -UseCulture automatically applies the system’s configured separator without manually specifying a delimiter character
