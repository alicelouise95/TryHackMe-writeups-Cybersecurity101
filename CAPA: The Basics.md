
### **TryHackMe: Cyber Security 101**

**Room:** `CAPA: The Bascs`  
**Status:** Completed  
**Date:** 2025-09-08

----------

### **Goal**

To learn the fundamentals of CAPA (Common Analysis Platform for Artifacts), understand its purpose in malware analysis, and practice interpreting its structured output to identify capabilities, behaviours, and techniques within executables.

---------

### **Key Topics Covered**

### 1. Introduction to CAPA

CAPA, developed by FireEye Mandiant, is a tool designed to automatically identify capabilities present in executable files such as Portable Executables (PE), ELF binaries, .NET modules, shellcode, and sandbox reports. It applies rules that encapsulate years of reverse engineering knowledge, making expert-level analysis more accessible.

The tool is especially useful in malware analysis and threat hunting, where understanding what a binary can do (e.g., network communication, file manipulation, process injection) is critical for incident response and defense.

Some commands and parameters noted:

-   `-h` or `--help`: Show help and exit
    
-   `-v` or `--verbose`: Enable verbose results
    
-   `-vv` or `--vverbose`: Enable very verbose results
    

Running CAPA on a file can produce lengthy outputs.

### 2. Example Output and File Information

When running CAPA against a binary (`cryptbot.bin` in this case), the first block of output contains fundamental file details:

-   Cryptographic hashes: MD5, SHA1, SHA256
    
-   Analysis type: e.g., static
    
-   OS: The operating system context (e.g., Windows)
    
-   Architecture: e.g., i386 (indicating x86)
    
-   Path: Location of the analyzed file
    

This baseline context is important because it sets the technical environment in which the file’s behaviours and capabilities are identified.

### 3. MITRE ATT&CK Integration

CAPA integrates with the MITRE ATT&CK framework, which is a global knowledge base documenting tactics and techniques used by adversaries. ATT&CK provides structure and identifiers for attacker behaviours across all stages of an intrusion.

CAPA outputs its ATT&CK references in the format:  
**ATT&CK Tactic::ATT&CK Technique::Technique Identifier**

Example:

-   Defense Evasion::Obfuscated Files or Information::T1027
    

This mapping allows defenders to connect file behaviours with known adversary tactics, narrowing down investigations and aligning analysis with industry-standard terminology.

### 4. MAEC (Malware Attribute Enumeration and Characterization)

MAEC is a standardized language for describing malware attributes and behaviours. CAPA uses MAEC values such as _launcher_ or _downloader_ to classify how malware operates.

-   **Launcher**: Behaviours like dropping payloads, activating persistence, connecting to C2 servers, or executing functions.
    
-   **Downloader**: Behaviours such as fetching payloads from the internet, retrieving configuration files, or executing secondary stages.
    

These categorizations provide a structured way of communicating what kind of malware activity is present.

### 5. Malware Behavior Catalogue (MBC)

MBC catalogs malware behaviours and objectives, supporting standardized analysis and reporting. It can link behaviours to ATT&CK but does not duplicate ATT&CK content.

CAPA presents MBC output in two formats:

-   `Objective::Behavior::Method[Identifier]`
    
-   `Objective::Behavior::[Identifier]`
    

Examples of **Objectives**:

-   Anti-Behavioral Analysis: Avoiding detection through sandbox or debugger evasion.
    
-   Command and Control: Establishing communications with compromised systems.
    
-   Defense Evasion: Bypassing security mechanisms.
    
-   Exfiltration: Stealing and extracting sensitive data.
    

**Micro-objectives** and **Micro-behaviors** represent low-level or non-malicious actions that malware often abuses. Examples include process creation, memory allocation, or string checking. Even though they aren’t inherently malicious, they form part of a larger malicious strategy.

### 6. Namespace

Namespaces in CAPA organize related rules under top-level categories (TLNs). For example:

-   **anti-analysis** TLN groups behaviours related to avoiding detection, such as obfuscation, packing, or anti-debugging.
    
-   Sub-namespaces include:
    
    -   `anti-vm/vm-detection`: Detects checks for virtual machines.
        
    -   `obfuscation`: Captures code obfuscation techniques.
        

Namespaces help analysts quickly locate and understand specific behaviour categories within CAPA’s structured output.

### 7. Capabilities

A capability describes a specific malware behaviour detected by CAPA. Each capability is tied to a namespace and a rule YAML file.

Examples:

-   **reference anti-VM strings**
    
    -   TLN: Anti-Analysis
        
    -   Namespace: anti-vm/vm-detection
        
    -   Rule: `reference-anti-vm-strings.yml`
        
    -   Meaning: Detects checks for VMware/VirtualBox artifacts.
        
-   **schedule task via schtasks**
    
    -   TLN: Persistence
        
    -   Namespace: scheduled-tasks
        
    -   Rule: `schedule-task-via-schtasks.yml`
        
    -   Meaning: Detects use of Windows scheduled tasks for persistence.
        

Some rules may appear in the _Nursery TLN_ (a staging area) rather than their logical TLN, e.g., cryptocurrency strings.

## What I Learned

-   CAPA automates reverse engineering knowledge into practical, structured analysis.
    
-   CAPA outputs key details: file info, ATT&CK mappings, MAEC values, MBC objectives/behaviours, namespaces, and capabilities.
    
-   MITRE ATT&CK provides a standardized mapping for adversary tactics and techniques.
    
-   MAEC categorizes malware as _launcher_ or _downloader_ to describe its role.
    
-   MBC catalogs behaviours and micro-behaviours to support consistent malware characterization.
    
-   Namespaces organize related malware behaviours, making CAPA’s results easier to interpret.
    
-   Capabilities describe specific malware actions and link directly to rule files.
