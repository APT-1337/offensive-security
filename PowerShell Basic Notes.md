
# ⚡ PowerShell Basic Notes

---

## 🧾 System Info Commands

| Command           | Description               |
|------------------|---------------------------|
| `$PSVersionTable` | Get PowerShell version     |
| `$Host`           | Information about the host |

---

## 📚 Cmdlet Basics

### 🔸 Get-Help

Useful for discovering how to use commands:

```powershell
Get-Help *process
Get-Help *service
Get-Help "alias"




	
 



- `Get-Help *process`: Shows help topics containing "process".
    
- `Get-Help *service`: Shows help topics related to "service".
    
- `Get-Help "alias"`: Shows help about aliases.
    
- `(Get-Alias | more)`: View all aliases with pagination.
    

### 🔸 Get-ChildItem

Used to list files and directories:

powershell

CopyEdit

`Get-ChildItem -Path /media/idont/APT/tel/TheGolden/ -Filter windows*`

- List all items starting with "windows" in the specified path.
    

powershell

CopyEdit

`Get-ChildItem -Attributes h`

- List all **hidden** files and folders.
    

---

## 🔍 Get-Command

Useful for discovering available commands:

powershell

CopyEdit

`Get-Command -Type Cmdlet -Name *copy*`

- Find all cmdlets with "copy" in the name.
    

powershell

CopyEdit

`Get-Command -Type Cmdlet | Measure-Object`

- Count all available cmdlets.
    

Example Output:



`Count : 255 
 Average           :
 Sum               :
 Maximum           :
 Minimum           :
 StandardDeviation :
 Property          :` 

---

## 🚀 Process Management

powershell

CopyEdit

`Start-Process notepad Stop-Process -Id 1234`

- `Start-Process <name>`: Launch a process (e.g., Notepad).
    
- `Stop-Process -Id <ID>`: Kill a process using its ID.
    

---

## 📁 Copy Files

powershell

CopyEdit

`Copy-Item "C:\example.txt" -Destination "D:\Backup\"`

- Copy a file or folder to a new location.
    

---



# 🎨 PowerShell Output Formatting

---

## 🧾 Overview

PowerShell outputs objects, not plain text. The **formatting system** defines how that output is displayed in the console. You can control how data is shown using **formatting cmdlets** or **output manipulation techniques**.

---

## 🔹 Common Formatting Cmdlets

### `Format-Table` (`ft`)
Displays output as a table.

```powershell
Get-Process | Format-Table Name, Id, CPU

- `-AutoSize`: Adjusts column width to fit content.
    
- `-Property`: Specify which properties to show.
    

Get-Process | Format-Table -Property Name, CPU -AutoSize



### `Format-List` (`fl`)

Displays output as a list of properties.

Get-Service | Format-List Name, Status
- Useful when objects have many properties.

### `Format-Wide` (`fw`)

Displays only one property per object in a wide format

Get-Command | Format-Wide Name -Column 3

## 🛠 Additional Output Cmdlets

### `Out-File`

Saves output to a file.

Get-Process | Out-File processes.txt

### `Export-Csv`

Exports objects as CSV.

Get-Service | Export-Csv -Path services.csv -NoTypeInformation

### `ConvertTo-Json`

Converts output to JSON format.

Get-Process | ConvertTo-Json

### `Select-Object`

Choose specific properties to output.

Get-Process | Select-Object Name, Id, CPU


## 🔁 Pipelining with Formatting

Always use formatting **at the end** of the pipeline.

❌ Incorrect:
Get-Process | Format-Table | Out-File wrong.txt

✅ Correct:
Get-Process | Out-File correct.txt

## 📌 Notes

- Formatting cmdlets (`Format-*`) are **for display only** – they turn objects into strings.
    
- Don't use them if you plan to **process the data further** (e.g., export or filter).

## 🧪 Practice Examples

# View services as a list
Get-Service | Format-List *

# Export all running processes as CSV
Get-Process | Where-Object {$_.CPU -gt 0} | Export-Csv processes.csv -NoTypeInformation

# Display command names in columns
Get-Command | Format-Wide Name -Column 4

