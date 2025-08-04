
### **TryHackMe: Cyber Security 101**

**Room:** `John the Ripper: The Basics`  
**Status:** Completed  
**Date:** 2025-08-04

----------

### **Goal**

Understand the fundamentals of hashing, hash security, and practical password cracking techniques using tools like John the Ripper. Learn how different hash formats work and how to identify, extract, and attack them using both built-in and custom strategies.

---------

### **Key Topics Covered**

**1. What Are Hashes?**

-   A **hash** is a fixed-length representation of data, created by passing input through a hashing algorithm.
    
-   Common algorithms include **MD4**, **MD5**, **SHA1**, and **NTLM**.
    
-   Regardless of input length, the output hash maintains a consistent length (e.g., MD5 outputs 32-character hashes).
    
-   Hashes are not meant to be reversible—they serve as digital fingerprints of the original data.
    

----------

**2. Hash Security and P vs NP**

-   Hashing is a **one-way function**, easy to compute but hard to reverse.
    
-   This concept is rooted in the **P vs NP** problem:
    
    -   **P**: Problems solvable in polynomial time.
        
    -   **NP**: Problems verifiable in polynomial time, but not necessarily solvable efficiently.
        
-   Reversing a hash is practically infeasible; brute-force attacks are used instead.
    

----------

**3. John the Ripper Overview**

-   **John the Ripper (John)** is a tool used to **crack hashed passwords** by performing dictionary attacks.
    
-   It hashes dictionary words and compares them to target hashes.
    
-   The tool supports various formats and attack types, depending on the system and installed version.
    

----------

**4. Installation of John the Ripper**

-   **Pre-installed** on Kali Linux and TryHackMe’s AttackBox.
    
-   On other systems, source compilation may be required for full features (Jumbo John).
    
-   **Windows users** can use precompiled binaries (32/64-bit).
    

----------

**5. Wordlists**

-   Effective cracking requires large, real-world **wordlists**.
    
-   **rockyou.txt** is a commonly used list sourced from a major data breach.
    
-   Located at `/usr/share/wordlists/` on Kali and AttackBox.
    
-   Can be extracted from **SecLists** on other platforms.
    

----------

**6. John Basic Syntax**

-   Format: `john [options] [path to file]`
    
-   Example: `john --wordlist=rockyou.txt hashes.txt`
    
-   Flags and options modify behavior for performance or specific attack types.
    

----------

**7. Automatic Cracking**

-   John can automatically detect hash formats and begin cracking:
    
    -   Example: `john --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt`
        
-   Automatic detection may fail for custom or unusual formats.
    

----------

**8. Identifying Hashes**

-   Use **hash-identifier** to detect hash formats when auto-detection fails.
    
-   Example usage:
    
    -   Run: `python3 hash-id.py`
        
    -   Enter hash when prompted to receive format suggestions.
        

----------

**9. Format-Specific Cracking**

-   Use the `--format` flag for known hash types:
    
    -   Example: `john --format=raw-md5 --wordlist=rockyou.txt hash.txt`
        
-   Run `john --list=formats` to view all supported formats.
    

----------

**10. NTHash/NTLM**

-   NTLM hashes are used in modern **Windows systems**.
    
-   Example command: `john --format=nt --wordlist=rockyou.txt ntlm_hash.txt`
    
-   Supports cracking Windows user credentials from SAM or NTDS.dit files.
    

----------

**11. Cracking /etc/shadow Hashes**

-   Combine `/etc/passwd` and `/etc/shadow` files with `unshadow`:
    
    -   Example: `unshadow passwd.txt shadow.txt > unshadowed.txt`
        
    -   Then: `john --format=sha512crypt --wordlist=rockyou.txt unshadowed.txt`
        

----------

**12. Single Crack Mode**

-   John mutates usernames from input files to generate guesses.
    
-   Format: `john --single --format=raw-sha256 hashes.txt`
    
-   Utilizes GECOS fields and known patterns for targeted attacks.
    

----------

**13. Custom Rules**

-   Use `--rules` to apply **mutation patterns** from configuration files.
    
-   Example: `john --wordlist=words.txt --rule=MyCustomRule hash.txt`
    
-   Rules mimic real-world password patterns (e.g., capital letters, digits, symbols).
    

----------

**14. zip2john**

-   Converts **ZIP file hashes** into a format John can crack.
    
-   Workflow:
    
    -   `zip2john archive.zip > zip_hash.txt`
        
    -   `john --wordlist=rockyou.txt zip_hash.txt`
        

----------

**15. rar2john**

-   Extracts hashes from **RAR archives** for cracking.
    
-   Command:
    
    -   `rar2john protected.rar > rar_hash.txt`
        
    -   `john --wordlist=rockyou.txt rar_hash.txt`
        

----------

**16. ssh2john**

-   Extracts password hashes from **encrypted SSH private keys**.
    
-   Usage:
    
    -   `/opt/john/ssh2john.py id_rsa > ssh_hash.txt`
        
    -   `john --wordlist=rockyou.txt ssh_hash.txt`
        
-   Recovers passphrases for SSH keys (useful in pentesting and CTFs).
    

----------

### **What I Learned**

-   Hashes are fixed-length, one-way representations of data.
    
-   Hashing is computationally irreversible but vulnerable to dictionary attacks.
    
-   John the Ripper is a flexible and powerful tool for cracking various hash types.
    
-   Custom rules and targeted wordlists improve cracking success.
    
-   Tools like zip2john, rar2john, and ssh2john convert encrypted files into John-compatible hashes.
    
-   Identifying the correct hash format is crucial for successful cracking.
    
-   Password storage and hash types differ across Windows, Linux, and application contexts.
