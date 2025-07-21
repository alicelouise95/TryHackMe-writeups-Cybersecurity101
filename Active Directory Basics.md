
### **TryHackMe: Cyber Security 101**

**Room:** `Active Directory Basics`  
**Status:** Completed  
**Date:** 2025-07-21

----------

### **Goal**

Understand the fundamental purpose of Microsoft’s Active Directory (AD), how it simplifies user and device management in corporate environments, and why domains and domain controllers are critical for scalable administration.

----------

### **Key Topics Covered**

#### **1. Active Directory Fundamentals**

-   **Purpose**: Centralizes management of users, computers, and policies in corporate networks.
    
-   **Domain Controller (DC)**: Hosts AD services; authenticates users and enforces policies.
    
-   **Why AD?**
    
    -   **Scalability**: Manages thousands of devices/users across multiple locations (vs. manual per-device configs).
        
    -   **Centralized Security**: Apply policies globally (e.g., restrict control panel access).
        
    -   **Example**: School/university networks use AD to validate credentials on any campus computer.
        

#### **2. AD Objects & Hierarchy**

-   **Objects**: Users, machines, printers, shares, etc.
    
    -   **Users**: Represent people or services (e.g., `MSSQL_Service`).
        
    -   **Machines**: Automatically created when devices join the domain. Named as `COMPUTERNAME$`.
        
-   **Organizational Units (OUs)**:
    
    -   Classify objects (e.g., `Sales`, `IT`) for targeted policy application.
        
    -   A user/machine can belong to **only one OU** (policy container).
        
-   **Security Groups**:
    
    -   Grant permissions to resources (e.g., shared folders).
        
    -   Users/machines can belong to **multiple groups**.
        
    -   **Key Groups**:
        
        -   `Domain Admins`: Full control over the domain.
            
        -   `Backup Operators`: Bypass file permissions for backups.
            
        -   `Account Operators`: Create/modify user accounts.
            

#### **3. Practical AD Management**

-   **Tools**:
    
    -   `Active Directory Users and Computers`: Manage OUs, users, groups.
        
    -   `Group Policy Management (GPO)`: Enforce policies (e.g., auto-lock screens).
        
-   **Delegation**: Grant limited admin rights (e.g., IT can reset passwords for specific OUs).
    
-   **GPO Distribution**:
    
    -   Policies sync via `SYSVOL` share (`C:\Windows\SYSVOL\sysvol\`).
        
    -   Force sync: `gpupdate /force`.
        

#### **4. Authentication Protocols**

-   **Kerberos (Default)**:
    
    1.  User requests **Ticket Granting Ticket (TGT)** from Key Distribution Center (KDC).
        
    2.  TGT used to request **Ticket Granting Service (TGS)** for specific services (e.g., file shares).
        
    3.  Service validates TGS using its account’s password hash.
        
-   **NetNTLM**: Legacy protocol (avoid if possible).
    

#### **5. Advanced AD Structures**

-   **Trees**: Multiple domains sharing a namespace (e.g., `corp.company.com` + `branch.company.com`).
    
-   **Forests**: Top-level container for domains with shared schema/security.
    
-   **Trusts**:
    
    -   Enable cross-domain resource access.
        
    -   Default: Two-way trust within a tree/forest.
        

----------

### **What I Learned**

-   **Centralization is Key**: AD eliminates manual device/user management at scale.
    
-   **Policy Power**: GPOs and OUs streamline security/configs across departments.
    
-   **Kerberos > NTLM**: Modern authentication is more secure and efficient.
    
-   **Delegation Matters**: Least-privilege access (e.g., password resets for IT) reduces risk.
    
-   **Forests/Trees**: Support complex enterprise structures with shared resources.
