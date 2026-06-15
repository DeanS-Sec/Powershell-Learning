Q1: Identify a CMmdlet that produces a random number

A:

Help *random*

Get-Help Get-Random -Examples
Get-Random

#Used the Help command with wildcard searching to identify cmdlets related to random number generation

#Discovered both Get-Random and Get-SecureRandom cmdlets

#Reviewed examples for each cmdlet using the -Examples parameter

#Observed that Get-Random is the more common/general-purpose cmdlet for generating random numbers

#Learned that Get-SecureRandom appears more security/cryptography focused

#Practiced using Get-Help and wildcard searches to discover available cmdlets

Q2: Identify a cmdlet that displays the current time and date

A:


Help *time*
Help *date*

Get-Help Get-Date -Examples
Get-Date

#Used wildcard searches with the Help command to identify cmdlets related to time and date functionality

#Observed that searching *time* did not immediately reveal the intended cmdlet

#Refined the search to *date* and identified the Get-Date cmdlet

#Used Get-Help with the -Examples parameter to review common usage examples

#Learned that Get-Date displays the current system date and time

#Practiced refining search terms when the initial wildcard search did not return the expected result

Q3: What type of object does the cmdlet from task 2 produce?

A:

Get-Date | Get-Member

Get-Date | gm

#Used Get-Member to inspect the object produced by the Get-Date cmdlet

#Learned that Get-Member displays the properties and methods available on an object

#Observed that the TypeName displayed at the top of the output was System.DateTime

#Identified that Get-Date produces a System.DateTime object

#Experimented with the Get-Member alias "gm"

#Observed that Select-Object without additional parameters did not significantly change the output object in this example

#Learned that PowerShell cmdlets output objects with properties and methods, not just plain text

Q4: Using the Cmdlet from task 2 and Select-Object, display only the current day of the week in a table like the following

A:

Get-Date | Select-Object DayOfWeek

Get-Date | Select-Object DayOfWeek | Format-Table

#Used the Get-Date cmdlet to retrieve the current system date and time object

#Used Select-Object to display only the DayOfWeek property from the System.DateTime object

#Observed that PowerShell automatically formatted the output as a table, even without explicitly using Format-Table

#Experimented with adding Format-Table to better understand PowerShell output formatting behavior

#Learned that Select-Object can be used to isolate and display specific object properties

#Reinforced the concept that PowerShell commands output objects with accessible properties

Q5: Identify a cmdlet that will show you all the times in a directory?

A:

Get-ChildItem "C:\Users\deanschauer\Documents\PowerShell Scripts" | Get-Member

Get-ChildItem "C:\Users\deanschauer\Documents\PowerShell Scripts" | Select-Object CreationTime, LastAccessTime, FullName

#Used Get-ChildItem to retrieve filesystem objects from a directory

#Initially experimented with Get-Date, but learned that Get-Date creates new DateTime objects rather than retrieving timestamp properties from files

#Used Get-Member to inspect the available properties of the System.IO.FileInfo objects returned by Get-ChildItem

#Identified time-related properties including:
#CreationTime
#LastAccessTime
#LastWriteTime

#Used Select-Object to display specific timestamp properties from the filesystem objects

#Included the FullName property to associate timestamps with specific files and folders

#Learned the distinction between:
#Get-Member = inspect available properties/methods
#Select-Object = display selected property values

#Reinforced the concept that filesystem items already contain metadata properties such as timestamps

Q6: Using the cmdlet from task 5, display all the times in the directory of your choice. Then extend the expression to sort the list by the time the items were created and displayed only tthe filenames and the date created. 

A:

Get-ChildItem "C:\Users\deanschauer\Documents\PowerShell Scripts" | Select-Object Name, CreationTime | Sort-Object -Stable CreationTime

#Used Get-ChildItem to retrieve filesystem objects from the selected directory

#Used Select-Object to display only the Name and CreationTime properties

#Initially experimented with FullName, but refined the output to use Name in order to display only filenames as requested by the lab

#Used Sort-Object to sort the filesystem objects by the CreationTime property

#Observed that the output was sorted from oldest to newest creation date

#Learned that Sort-Object requires a property name to determine how objects should be ordered

#Experimented with the -Stable parameter and reviewed additional sorting options such as -Descending

#Reinforced the pipeline workflow:
#Get objects -> Select properties -> Sort objects -> Display output

Q7: Repeat task 6, but this time sort the items by the last write time, then display the filename, creatinetime, and the last write time. Save at CSV or HTML.

A:

Get-ChildItem "C:\Users\deanschauer\Documents\PowerShell Scripts" |
Select-Object Name, CreationTime, LastWriteTime |
Sort-Object -Stable LastWriteTime |
Export-Csv -Path "C:\Users\deanschauer\Documents\PowerShell Scripts\L8Q7.csv"

#Used Get-ChildItem to retrieve filesystem objects from the selected directory

#Used Select-Object to display only the Name, CreationTime, and LastWriteTime properties

#Used Sort-Object to sort the objects by the LastWriteTime property

#Initially experimented with Out-File and ConvertTo-Csv, but learned that Out-File produces plain text output rather than a structured CSV file

#Learned that Export-Csv is the proper PowerShell cmdlet for exporting structured object data into CSV format

#Observed that pipeline order matters when transforming and exporting objects

#Verified that the exported CSV opened correctly in Excel with properly separated columns and structured data

#Reinforced the PowerShell object pipeline workflow:
#Retrieve objects -> Select properties -> Sort objects -> Export structured data
