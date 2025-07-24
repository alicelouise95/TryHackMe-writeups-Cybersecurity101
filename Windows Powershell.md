
### **TryHackMe: Cyber Security 101**

**Room:** `Windows Powershell`  
**Status:** Completed  
**Date:** 2025-07-23

----------

### **Goal**
Gain hands-on familiarity with Microsoft PowerShell. Powershell is a cross-platform, object-oriented shell and scripting language used for navigating the file system, processing data, querying system/network information, and automating administrative tasks.

### **Key Topics Covered**


**1. Introduction to PowerShell**

-   PowerShell is a CLI and scripting environment built on the .NET framework. It’s designed for task automation and configuration management.
    
-   PowerShell supports Windows, macOS, and Linux.
    
-   Cmdlets follow a consistent `Verb-Noun` format, e.g.:
    
    -   `Get-Content` (`gc`) — displays contents of a file.
        
    -   `Set-Location` — changes the current directory.
        
-   Use `Get-Command` to list available cmdlets, functions, aliases, and scripts. Example:
    
    -   `Get-Command -CommandType Function`
        
-   Use `Get-Help` for cmdlet documentation, with options like:
    
    -   `-Examples` to show usage scenarios.
        
-   View command aliases with `Get-Alias`. Example:
    
    -   `Clear-Content` = `clc`
        
    -   `Set-Location` = `cd` / `chdir`
        
-   Download additional modules using `Find-Module`. Example:
    
    -   `Find-Module -Name "PowerShell*"`
        

----------

**2. Navigating the File System**

-   Basic file system cmdlets include:
    
    -   `Get-Content`, `Get-ChildItem` (`ls`/`dir`), `New-Item`, `Remove-Item`, etc.
        
-   Tasks involved opening files, reading text, listing directory contents, creating/removing files, and jumping between folders.
    

----------

**3. Piping, Filtering, and Sorting**

-   The pipe `|` sends the output of one cmdlet to another.
    
-   `Sort-Object` sorts objects by a specified property. Example:
    
    -   `ls | Sort-Object Length`
        
-   `Where-Object` filters based on conditionals:
    
    -   `ls | Where-Object -Property Extension -eq ".txt"`
        
    -   Other comparisons:
        
        -   `-ne`: not equal
            
        -   `-gt`: greater than
            
        -   `-ge`: greater than or equal
            
        -   `-lt`: less than
            
        -   `-le`: less than or equal
            
-   `Select-Object` chooses specific properties:
    
    -   `ls | Select-Object Name, Length`
        
-   Task: Display the largest file in `C:\Users\captain\Documents\captain-cabin`.
    
    -   My solution:  
        `ls | Where-Object -Property "Length" -ge 265`  
        (based on file sizes I had already observed)
        
    -   Expected answer:  
        `ls | Sort-Object Length -Descending | Select-Object -First 1`
        

----------

**4. Searching Text**

-   `Select-String` searches inside files (like `grep`):
    
    -   `Select-String -Path ".\example-file.txt" -Pattern "exampletext"`
        
    -   Output includes the filename, line number, and matched line.
        

----------

**5. System & Network Information**

-   `Get-ComputerInfo` — returns system-wide info: OS, BIOS, CPU, etc.
    
-   `Get-LocalUser` — lists local user accounts.
    
-   `Get-NetIPConfiguration` — shows active network interfaces and DNS/gateway info.
    
-   `Get-NetIPAddress` — returns all configured IP addresses.
    

----------

**6. Real-Time System Analysis**

-   `Get-Process` — shows running processes with CPU and memory usage.
    
-   `Get-Service` — displays service status (running/stopped/paused).
    
-   `Get-NetTCPConnection` — lists active TCP connections (useful for detecting suspicious remote connections).
    
-   `Get-FileHash` — computes hash values for files (useful for integrity verification during incident response).  
    _(Not totally sure how to use it in practice yet, but I get the idea.)_
    

----------

**7. Scripting & Automation**

-   PowerShell scripts are `.ps1` files containing a series of commands for automation.
    
-   **Blue team** uses include:
    
    -   Automating log analysis
        
    -   Extracting indicators of compromise
        
    -   Malware reverse engineering
        
-   **Red team** uses include:
    
    -   Automating enumeration and remote execution
        
    -   Obfuscation techniques
        
    -   Deploying payloads
        
-   `Invoke-Command` allows execution of commands on remote systems:
    
    -   `Invoke-Command -ComputerName <target> -ScriptBlock { ... }`
        

----------

### **What I Learned**

-   PowerShell is far more than a shell — it’s a fully-fledged scripting language capable of interacting with the OS, services, processes, files, and network interfaces.
    
-   Cmdlets follow a clear and consistent pattern that makes it easy to learn new ones.
    
-   Filtering, sorting, and selecting objects via the pipeline is incredibly powerful when analyzing output.
    
-   PowerShell is a must-know for both blue and red teams — for automation, investigation, or exploitation.
    
-   I liked that I was able to problem-solve differently than the expected solution in some places and still get valid results.
