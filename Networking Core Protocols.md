
### **TryHackMe: Cyber Security 101**

**Room:** `Networking Core Protocols`  
**Status:** Completed  
**Date:** 2025-07-27

----------

### **Goal**

Gain hands-on experience with core network protocols like DNS, HTTP/S, FTP, SMTP, POP3, and IMAP, understanding how they function, what ports they use, and how they’re used in real-world communication across the internet.

----------


### **Key Topics Covered**


**1. DNS (Domain Name System)**

DNS resolves domain names to IP addresses, acting as the internet’s “phonebook.”

**Protocol Details:**

-   Operates at **Layer 7 (Application Layer)**
    
-   Uses **UDP port 53** by default; **TCP port 53** as fallback
    
-   Can be queried using tools like `nslookup`
    

**Common DNS Records:**

-   `A` – Maps domain to IPv4 address
    
-   `AAAA` – Maps domain to IPv6 address
    
-   `CNAME` – Maps one domain to another (e.g. `www.example.com` → `example.com`)
    
-   `MX` – Defines mail servers for a domain
    

----------

**2. WHOIS**

WHOIS allows you to query ownership information about domain names.

**Usage:**

-   Reveals registrar, contact email, phone number, and organization info
    
-   Helpful for OSINT, domain investigations, and identifying malicious actors
    

----------

**3. HTTP and HTTPS**

HTTP(S) defines how browsers and servers communicate. It’s used for accessing web content.

**Protocol Details:**

-   Relies on **TCP**
    
-   Common ports:
    
    -   **HTTP** → Port **80**
        
    -   **HTTPS** → Port **443**
        
    -   Others: **8080**, **8443**
        

**Request Methods:**

-   `GET` – Retrieve data (HTML, images, etc.)
    
-   `POST` – Submit data (forms, uploads)
    
-   `PUT` – Create or overwrite data
    
-   `DELETE` – Delete a resource
    

**Practical Task:**

-   Used `telnet` to connect to a web server and retrieve a flag using a manual HTTP `GET` request.
    

----------

**4. FTP (File Transfer Protocol)**

FTP enables file transfers between a client and a server.

**Protocol Details:**

-   Uses **TCP port 21**
    
-   Supports login with `USER` and `PASS`
    
-   Key commands:
    
    -   `RETR` – Download file
        
    -   `STOR` – Upload file
        
    -   `ls` – List directory contents
        
    -   `type ascii` – Switch to ASCII mode for text files
        
    -   `get flag.txt` – Retrieve target file
        

**Practical Task:**

-   Connected to the target FTP server (no login required), listed files, switched to ASCII mode, and downloaded `flag.txt`.
    

----------

**5. SMTP (Simple Mail Transfer Protocol)**

SMTP is used for **sending** emails between clients and servers.

**Protocol Details:**

-   Uses **TCP port 25**
    
-   Common Commands:
    
    -   `HELO` / `EHLO` – Initiate session
        
    -   `MAIL FROM` – Set sender
        
    -   `RCPT TO` – Set recipient
        
    -   `DATA` – Begin writing the message
        
    -   `.` – Ends the message
        

----------

**6. POP3 (Post Office Protocol v3)**

POP3 is used for retrieving emails **from a server to a local client**.

**Protocol Details:**

-   Uses **TCP port 110**
    
-   Common Commands:
    
    -   `USER` – Specify username
        
    -   `PASS` – Provide password
        
    -   `STAT` – Get mailbox stats
        
    -   `LIST` – List messages
        
    -   `RETR <n>` – Retrieve message `n`
        
    -   `DELE <n>` – Mark message for deletion
        
    -   `QUIT` – End session
        

**Practical Task:**

-   Used `telnet` to connect to the POP3 server and log in using provided credentials.
    
-   Retrieved message 4 using `RETR 4` to obtain the flag.
    

----------

**7. IMAP (Internet Message Access Protocol)**

IMAP allows for remote access to email messages while keeping them on the server.

**Protocol Details:**

-   Uses **TCP port 143**
    
-   Designed for **synchronization** across devices
    
-   Unlike POP3, it doesn't delete mail upon download
    

**Common Commands:**

-   `LOGIN <username> <password>` – Authenticate
    
-   `SELECT <mailbox>` – Choose mailbox
    
-   `FETCH <n> body[]` – Retrieve full message `n`
    
-   `MOVE` / `COPY` – Manage messages between folders
    
-   `LOGOUT` – End session
    

----------

### **What I Learned**

-   Gained a practical understanding of core application-layer protocols used in networking
    
-   Learned the difference between protocols for retrieving vs. sending email (POP3, IMAP, SMTP)
    
-   Practiced using `telnet`, `ftp`, and `nslookup` for manual interactions with common services
    
-   Became familiar with various port numbers and protocol behaviors
    
-   Strengthened confidence in navigating and investigating network services manually
