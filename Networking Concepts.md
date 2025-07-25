
### **TryHackMe: Cyber Security 101**

**Room:** `Networking Concepts`  
**Status:** Completed  
**Date:** 2025-07-25

----------

### **Goal**

Understand core networking concepts including the OSI and TCP/IP models, IP addressing and subnets, transport protocols (TCP and UDP), encapsulation, and basic use of Telnet for remote connections.

----------


### **Key Topics Covered**


**1. OSI Model Layers**

-   **Physical Layer (Layer 1):** Handles the physical connection—wires, cables, antennas—and how bits (0s and 1s) are transmitted as electrical, optical, or wireless signals.
    
-   **Data Link Layer (Layer 2):** Defines protocols for communication between nodes on the same network segment (devices sharing the same channel). It controls how devices communicate over a shared medium.
    
-   **Network Layer (Layer 3):** Responsible for logical addressing and routing data across multiple networks. Key protocols include IP, ICMP, and VPN protocols like IPSec and SSL/TLS.
    
-   **Transport Layer (Layer 4):** Ensures reliable data transfer between processes on networked hosts.
    
-   **Session Layer (Layer 5):** Establishes, maintains, and synchronizes sessions (connections) between applications on different hosts.
    
-   **Presentation Layer (Layer 6):** Handles data encoding, compression, and encryption, so data is in a usable format (e.g., ASCII, Unicode).
    
-   **Application Layer (Layer 7):** Provides network services directly to user applications like web browsers using protocols such as HTTP.
    

----------

**2. TCP/IP Model**

-   Groups OSI layers 5, 6, and 7 into a single **Application Layer**.
    
-   Has **Transport Layer** (same as OSI Layer 4).
    
-   Has **Internet Layer** (equivalent to OSI Network Layer).
    
-   Has **Link Layer** (combining OSI’s Data Link and Physical layers).
    

----------

**3. IP Addresses and Subnets**

-   Each host needs a **unique IP address** to be identified on the network.
    
-   IP addresses are **32-bit** numbers divided into four octets (e.g., 192.168.1.1). Each octet ranges from 0–255.
    
-   **Network address** and **broadcast address** are reserved; e.g., in 192.168.1.0/24, `.0` is network address, `.255` is broadcast.
    
-   **Subnet mask** (e.g., 255.255.255.0 or `/24`) defines which part of the IP address represents the network.
    
-   IP addresses are either **public** (routable on the Internet) or **private** (used inside local networks). NAT (Network Address Translation) allows private IPs to communicate via a router’s public IP.
    

----------

**4. UDP vs TCP**

-   **UDP (User Datagram Protocol):** Connectionless, no handshake, no guarantee packets arrive or arrive in order. Lightweight, faster.
    
-   **TCP (Transmission Control Protocol):** Connection-oriented, reliable, uses sequence numbers and acknowledgments to ensure ordered delivery.
    
-   **TCP Three-Way Handshake:**
    
    1.  **SYN:** Client sends synchronization packet with initial sequence number.
        
    2.  **SYN-ACK:** Server responds with its own sequence number and acknowledgment.
        
    3.  **ACK:** Client acknowledges server’s SYN-ACK, establishing the connection.
        

----------

**5. Encapsulation**

Data travels down the layers by being encapsulated:

-   **Application Data:** The original user data from an application (e.g., email text).
    
-   **Transport Segment/Datagram:** Transport layer adds headers (TCP/UDP).
    
-   **Network Packet:** Network layer adds IP headers.
    
-   **Data Link Frame:** Data link layer adds Ethernet/WiFi headers and trailers for physical transmission.
    

----------

**6. Telnet**

-   A simple protocol for remote terminal connections via text commands.
    
-   It operates without encryption, making it insecure for sensitive data.
    
-   Tested connections to ports 7 (Echo), 13 (Daytime), and 80 (HTTP) on a virtual machine, observing the returned responses.
    

----------

### **What I Learned**

-   Gained a clear understanding of the layered network models (OSI and TCP/IP) and how they map to real-world protocols.
    
-   Understood the importance and structure of IP addressing and subnetting.
    
-   Explored the fundamental differences between UDP and TCP transport protocols and how TCP connections are established.
    
-   Learned about data encapsulation and how each layer adds its own header/trailer for successful communication.
    
-   Practiced using Telnet to connect remotely and saw firsthand why encryption is important in network communications.
    




