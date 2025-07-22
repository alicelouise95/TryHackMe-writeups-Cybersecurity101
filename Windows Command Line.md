
### **TryHackMe: Cyber Security 101**

**Room:** `Windows Command Line`  
**Status:** Completed  
**Date:** 2025-07-22

----------

### **Goal**
Develop familiarity with the Windows command line interface (CLI), including how to navigate the file system, manage tasks, gather system/network information, and troubleshoot issues, all from the terminal. 

### **Key Topics Covered**

**1. Basic System Information**

-   Use the `set` command to view environment variables. The `Path=` variable shows where Windows searches for executables.
    
-   `ver` provides the Windows version.
    
-   `systeminfo` displays detailed information such as OS version, architecture, memory, and network configuration.
    
-   Long outputs can be piped into pages using `| more` for easier readability.
    

----------

**2. Network Troubleshooting**

-   `ipconfig` shows basic network interface info. Use `ipconfig /all` for extended details such as DNS servers and DHCP status.
    
-   `ping <target>` checks connectivity by sending ICMP packets and measuring response times.
    
-   `tracert <target>` reveals the path packets take to a destination, showing each hop along the route.
    
-   `nslookup <domain>` retrieves DNS information (e.g., resolving domains to IPs). You can specify a DNS server: `nslookup example.com 1.1.1.1`
    
-   `netstat` shows current network connections and listening ports. Common arguments include:
    
    -   `-a`: Shows all connections and listening ports
        
    -   `-b`: Displays the executable associated with each connection
        
    -   `-o`: Displays the PID for each connection
        
    -   `-n`: Displays addresses and ports numerically
        
-   Practical examples included:
    
    -   Finding the MAC address with `ipconfig /all`
        
    -   Identifying the service bound to port 3389 (RDP → TermService)
        
    -   Verifying subnet mask
        

----------

**3. File and Disk Management**

-   Navigate directories with `cd`, and list contents using `dir`.
    
    -   `dir /a` shows hidden/system files
        
    -   `dir /s` shows contents of current and subdirectories
        
-   `tree` displays a visual structure of folders and subfolders.
    
-   Directory and file operations:
    
    -   `mkdir` / `rmdir`: Create/delete directories
        
    -   `type <file>`: View contents of a text file
        
    -   `copy <source> <destination>`: Copy files
        
    -   `move <source> <destination>`: Move files
        
    -   `del` or `erase`: Delete files
        
    -   `*` wildcard: Match multiple files (e.g., `*.txt`)
        

----------

**4. Task and Process Management**

-   `tasklist` shows running processes.
    
-   Use `/FI` (filter) to refine results:
    
    -   Example: `tasklist /FI "imagename eq sshd.exe"` filters processes by name.
        
-   Once a process is identified, terminate it with its PID using `taskkill /PID <pid_number>`.
    
-   Use `tasklist /?` to see all possible arguments and filters.
    

----------

### What I Learned

-   The Windows command line is a powerful tool for viewing system information, managing files, inspecting networks, and handling processes.
    
-   I now understand how to trace network paths, resolve DNS entries, and read into current network connections and their associated programs.
    
-   File operations are intuitive, and wildcard support is helpful for working with multiple files at once.
    
-   Tasklist and taskkill allow fine control over processes, useful for both system administration and forensic analysis.
    
-   Learning to pipe output with `| more` and using modifiers like `/all`, `/FI`, or wildcards greatly enhances usability of terminal commands.
