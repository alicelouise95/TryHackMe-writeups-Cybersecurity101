
### **TryHackMe: Cyber Security 101**

**Room:** `Metasploit: Meterpreter`  
**Status:** Completed  
**Date:** 2025-08-08

----------

### **Goal**

Understand the fundamentals of Meterpreter, its different versions, functionalities, and usage in post-exploitation, while practicing practical exploitation steps using Metasploit to gain access to and interact with a target system.

---------

### **Key Topics Covered**


**1. Meterpreter Overview**

Meterpreter is a Metasploit payload that acts as an advanced, in-memory agent for post-exploitation tasks. It allows penetration testers to interact with a target operating system, manipulate files, capture data, and execute commands without writing itself to disk, enhancing stealth against antivirus software.  
Key points include:

-   Runs entirely in RAM to avoid detection by disk-based antivirus scans.
    
-   Uses encrypted communication (TLS) to evade network-based IDS/IPS detection.
    
-   Available in multiple versions for platforms such as Windows, Linux, macOS, Android, PHP, Python, Java, and iOS.
    
-   Payloads can be **staged** (delivered in two parts) or **inline** (delivered in a single step).
    
-   Selection of a Meterpreter version depends on target OS, available components, and permitted network connections.
    

----------

**2. Meterpreter Commands and Categories**

The `help` command displays available commands, grouped into categories such as:

-   **Core Commands** – e.g., `background`, `migrate`, `sessions`, `load`.
    
-   **File System Commands** – e.g., `cd`, `ls`, `cat`, `upload`, `download`.
    
-   **Networking Commands** – e.g., `arp`, `ifconfig`, `portfwd`, `netstat`.
    
-   **System Commands** – e.g., `sysinfo`, `ps`, `execute`, `getuid`, `hashdump`.
    
-   **User Interface & Peripheral Commands** – e.g., `screenshot`, `record_mic`, `webcam_snap`.
    

Not all commands work on every system, as hardware or environment limitations may apply.

----------

**3. Post-Exploitation Tools and Techniques**

Meterpreter’s post-exploitation capabilities include:

-   **Privilege escalation** (e.g., `getsystem`).
    
-   **Credential extraction** (e.g., `hashdump`).
    
-   **Process migration** for stability or capturing keystrokes.
    
-   **File searches** using the `search` command.
    
-   **Spawning shells** for direct OS command execution.
    

These tools support gathering intelligence, maintaining persistence, and preparing for lateral movement.

----------

**4. Practical Exercise: Exploiting a Target via SMB**

**Step 1 – Initial Exploitation**

-   Located the `exploit/windows/smb/psexec` module in `msfconsole`.
    
-   Used `show options` to configure required settings, including:
    
    -   `RHOST` – target host IP.
        
    -   Credentials provided by the challenge.
        
-   Executed the exploit to obtain a Meterpreter session.
    

**Step 2 – Identifying System Information**

-   Ran `sysinfo` within Meterpreter to retrieve the computer name.
    

**Step 3 – Gathering Domain Information**

-   Backgrounded the session.
    
-   Used the `post/windows/gather/enum_domain` module, set the `SESSION` parameter, and executed it to identify the target domain.
    

**Step 4 – Enumerating Network Shares**

-   Used the `post/windows/gather/enum_shares` module to list network shares, identifying one likely created by the user.
    

**Step 5 – Extracting NTLM Hashes**

-   Ran `hashdump` in Meterpreter to obtain the NTLM hash of the specified user account.
    

**Step 6 – Locating Files**

-   Used `search -f secrets.txt` to locate the `secrets.txt` file.
    

**Step 7 – Reading File Contents**

-   Attempted `cat` in Meterpreter, but encountered “The system cannot find the file specified.”
    
-   Opened an OS-level shell using `shell`, navigated to the directory, and used `type` to view the file contents.
    

**Step 8 – Repeating for Additional Files**

-   Repeated the process for `realsecret.txt` to find its location and reveal its contents.
    

This structured approach combined automated post-exploitation modules, manual searching, and shell-level interaction to answer all provided challenge questions.

----------

### **What I Learned**

-   Meterpreter operates in memory, enhancing stealth against traditional antivirus solutions.
    
-   TLS-encrypted communication can evade some IDS/IPS systems if traffic inspection is not implemented.
    
-   Payload choice depends on the target OS, available components, and network restrictions.
    
-   The `help` command is essential for quickly understanding available Meterpreter capabilities.
    
-   Staged payloads allow smaller initial delivery, while inline payloads send all data at once.
    
-   Process migration can improve session stability and enable advanced techniques such as keylogging.
    
-   Post-exploitation modules in Metasploit can automate common information-gathering tasks.
    





