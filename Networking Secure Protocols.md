
### **TryHackMe: Cyber Security 101**

**Room:** `Networking Secure Protocols`  
**Status:** Completed  
**Date:** 2025-07-28

----------

### **Goal**

Understand the importance of securing network communication using encrypted protocols such as TLS, HTTPS, SSH, SFTP, FTPS, and VPNs, ensuring data confidentiality, integrity, and authentication in transit.

----------



### **Key Topics Covered**

**1. TLS (Transport Layer Security)**

Originally developed as SSL in 1995 to protect against eavesdropping and packet sniffing. TLS succeeded SSL in 1999 and is now the standard, with TLS 1.3 being the most secure version.

**TLS ensures:**

-   Confidentiality – No unauthorized reading of data
    
-   Integrity – No undetected tampering or modification
    
-   Authentication – Servers (and optionally clients) prove their identity via certificates
    

**Protocols using TLS include:**

-   HTTP becomes HTTPS
    
-   DNS becomes DoT (DNS over TLS)
    
-   MQTT becomes MQTTS
    
-   SIP becomes SIPS
    

**TLS Certificates:**  
Websites present a certificate to prove identity.  
Browsers and clients validate this using pre-installed Trusted Certificate Authorities (CAs).

----------

**2. HTTPS**

HTTP on port 80 sends data in cleartext.  
HTTPS on port 443 secures HTTP traffic using TLS encryption.

**Process:**

1.  TCP Handshake
    
2.  TLS Session Establishment
    
3.  HTTP over Encrypted Channel
    

**Why it matters:**  
Even with packet capture tools like Wireshark, intercepted HTTPS traffic appears as gibberish unless the decryption key is available.

----------

**3. Secure Protocols and Ports**

-   HTTP uses port 80 and becomes HTTPS on port 443
    
-   SMTP uses port 25 and becomes SMTPS on ports 465 or 587
    
-   POP3 uses port 110 and becomes POP3S on port 995
    
-   IMAP uses port 143 and becomes IMAPS on port 993
    

----------

**4. SSH (Secure Shell)**

Replaces Telnet for remote terminal access. Encrypts all communication.

**Timeline:**

-   1995 – SSH-1 released
    
-   1996 – SSH-2 introduced (improved security)
    
-   1999 – OpenSSH released (open-source, widely used today)
    

**Benefits of SSH:**

-   Secure authentication (password, public key, 2FA)
    
-   Encrypted traffic
    
-   Integrity checks
    
-   Tunneling (e.g., secure web browsing, database access)
    
-   X11 Forwarding – Run GUI apps remotely using `ssh -X`
    

SSH uses port 22. It warns if server keys change to help prevent man-in-the-middle attacks.

----------

**5. SFTP vs FTPS**

SFTP is a secure file transfer method that runs over SSH.  
FTPS is FTP with TLS encryption.

**SFTP:**

-   Uses SSH
    
-   Uses port 22
    
-   Encrypted traffic
    
-   Integrates with OpenSSH
    
-   Uses SSH authentication methods like passwords and keys
    
-   Simple setup if SSH is already enabled
    
-   Easier to configure with firewalls
    

**FTPS:**

-   Based on FTP
    
-   Uses port 990 for control and separate ports for data
    
-   Uses TLS encryption
    
-   Requires TLS certificates
    
-   More familiar to FTP users
    
-   Harder to configure due to certificate management and multiple ports
    

----------

**6. VPN (Virtual Private Network)**

VPNs create encrypted tunnels between networks or devices.

**Why VPNs are used:**

-   Secure communication across public networks
    
-   Hide real IP address by replacing it with the VPN server’s IP
    
-   Prevent local ISPs from inspecting or censoring traffic
    
-   Allow remote branches or devices to connect to the main office network
    

**Without a VPN:**  
TCP traffic can be intercepted and manipulated.

**With a VPN:**  
All traffic is routed through a secure, private tunnel, protecting both confidentiality and integrity.

----------

### **What I Learned**

-   Understood how TLS evolved from SSL and now secures many protocols
    
-   Learned the difference between HTTP and HTTPS, and why encryption matters
    
-   Looked at default port numbers for both secure and insecure versions of key protocols
    
-   Grasped the role of SSH and its advantages over Telnet for secure terminal access
    
-   Compared SFTP and FTPS in terms of deployment, security, and complexity
    
-   Realized how VPNs protect data and provide privacy across insecure networks
    

