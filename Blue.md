
### **TryHackMe: Cyber Security 101**

**Room:** `Blue`  
**Status:** Completed  
**Date:** 2025-08-09

----------

### **Goal**

Complete a practical exploitation of a Windows machine vulnerable to EternalBlue by scanning, exploiting, escalating privileges, dumping hashes, cracking passwords, and finding flags.

---------

### **Practical Walkthrough**

**"Scan the machine. How many ports are open with a port number under 1000?"**  
I ran `nmap -sV <target-ip>` and found **3 ports open** under port 3000, including port 445.

**"What is this machine vulnerable to?"**  
Since port 445 was open, I ran `nmap -p445 --script smb-vuln-ms17-010 <target-ip>` which showed the machine was vulnerable to **ms17-010 (EternalBlue)**.

**"Find the exploitation code we will run against the machine. What is the full path of the code?"**  
In Metasploit, I used `search eternalblue` and found the exploit located at **exploit/windows/smb/ms17_010_eternalblue**.

**"Show options and set the one required value. What is the name of this value?"**  
Running `show options` revealed I needed to set **RHOSTS** to the target IP address.

**"What payload did you set?"**  
I set the payload to **windows/x64/shell/reverse_tcp** before running the exploit.

**"Confirm the exploit ran correctly."**  
The shell opened successfully, confirming the exploit worked. I then backgrounded the session.

**"What is the name of the post module to convert the shell to a meterpreter shell?"**  
I searched `search meterpreter shell` and found **post/multi/manage/shell_to_meterpreter**.  
Setting the `SESSION` to the shell session upgraded it to a Meterpreter shell.

**"Verify you have escalated to NT AUTHORITY\SYSTEM."**  
I ran `getsystem` which confirmed I was already running as **NT AUTHORITY\SYSTEM**.  
I also opened a DOS shell (`shell`) and ran `whoami` to verify the same, then backgrounded the shell.

**"Choose a process and migrate to it."**  
Using `ps`, I found the process **svspool.exe** and migrated to its PID with `migrate <PID>`.

**"Run hashdump and find the non-default user."**  
Running `hashdump` showed the non-default user was **Jon**.

**"Crack Jon’s password hash."**  
I saved Jon’s hash to a file using `nano`, then cracked it with John the Ripper using:
`john -- Jonhash.txt --format=NT --wordlist=/usr/share/wordlists/rockyou.txt`
The cracked password was **alqfna22**.

**"Where is flag1.txt located and what is the flag?"**  
I ran `search -f flag1.txt` to find the file at the system root and revealed its contents with `cat`, showing **flag{access_the_machine}**.

**"Where is flag2.txt located and what is the flag?"**  
Similarly, `search -f flag2.txt` located it in the Windows password storage location. Using `cat` revealed the flag **flag{access_the_machine}**.

**"Where is flag3.txt located and what is the flag?"**  
I found `flag3.txt` in an administrator’s directory by searching and viewing with `cat`, revealing **flag{access_the_machine}**.

----------

### **What I Practiced**

-   Scanning a target and identifying SMB-related vulnerabilities using nmap and scripts.
    
-   Locating and configuring the correct Metasploit exploit and payload.
    
-   Exploiting MS17-010 and upgrading a shell to Meterpreter.
    
-   Methods to verify privilege escalation and migrate processes for stability.
    
-   Techniques to dump password hashes and crack them offline.
    
-   Searching for and reading flag files systematically.

