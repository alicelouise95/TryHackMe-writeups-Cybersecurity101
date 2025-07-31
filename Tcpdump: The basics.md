
### **TryHackMe: Cyber Security 101**

**Room:** `Tcpdump: The basics`  
**Status:** Completed  
**Date:** 2025-07-30

----------

### **Goal**

Learn how to use `tcpdump` to capture, read, filter, and analyze network traffic directly from the terminal using command-line syntax and filters.

---------

### **Key Topics Covered**


**1. What is Tcpdump?**

Tcpdump is a command-line packet analyzer used to capture and inspect network traffic. It is lightweight, fast, and often used for quick inspections or automated scripts.

**Key characteristics:**

-   Runs in terminal, no GUI

-   Can read from live traffic or saved `.pcap` files
    
-   Works on most Unix-like systems
    

----------

**2. Capturing Live Traffic**

Basic syntax: `tcpdump -i [interface]`

-   `-i eth0`: Capture from the `eth0` interface
    
-   `-i any`: Capture from all interfaces
    
-   You can view available interfaces using `tcpdump -D`
    

Use `sudo` for permissions to capture live traffic.

----------

**3. Saving & Reading PCAP Files**

- To save captures to a file: `tcpdump -i eth0 -w capture.pcap`

- To read and display a saved capture: `tcpdump -r capture.pcap`

Useful for later analysis or sharing with other tools like Wireshark.

**4. Packet Filtering**

-   `tcp`: Capture only TCP packets
    
-   `udp port 53`: Capture DNS traffic
    
-   `host 192.168.0.1`: Filter packets to or from specific IP
    
-   `net 10.0.0.0/8`: Capture all traffic on a subnet
    
-   `src port 80`: Filter packets **from** port 80
    
-   `dst port 443`: Filter packets **to** port 443
    

**Combining filters:**

-   `and`, `or`, `not` — logical operators
    
-   `tcp and port 80 and not src 192.168.1.10`
    

----------

**5. Verbosity Options**

Control the level of packet detail shown:

-   `-v`: Verbose
    
-   `-vv`: More verbose
    
-   `-vvv`: Maximum detail (e.g., TTL, window size, flags)
    

Use higher verbosity for protocol-specific insight.

----------

**6. Limiting Output**

-   `-c 100`: Capture only 100 packets
    
-   `-n`: Don’t resolve hostnames (speeds up analysis)
    
-   `-nn`: Don’t resolve hostnames or port names
    
Useful for scripting, performance, or focusing on raw output.

----------

**7. Packet Snap Length**

By default, only part of each packet is captured. Use `-s` to control **snap length** (max bytes to capture):

-   `-s 0`: Capture full packets
    
-   `-s 96`: Capture first 96 bytes (common default)
    
Lower values improve performance but might miss payload data.

----------

**8. Displaying Hex Output**

-   `-X`: Show packet contents in both HEX and ASCII
    
-   `-XX`: Same as `-X`, plus Ethernet headers
    

Great for examining low-level contents (e.g., HTTP requests, binary data).

----------

**9. Filtering by Protocol**

Some quick examples:

-   `icmp`: Ping and other ICMP traffic
    
-   `arp`: Address Resolution Protocol
    
-   `tcp port 80`: HTTP traffic
    
-   `udp port 53`: DNS queries
    
-   `port 22`: SSH (both TCP and UDP)
    

----------

**10. Real-Time Analysis Use Cases**

Tcpdump is often used for:

-   Troubleshooting connection issues
    
-   Verifying data is being sent/received on correct ports
    
-   Monitoring unauthorized traffic
    
-   Capturing quick evidence before deeper analysis in tools like Wireshark
    

----------

### **What I Learned**

-   Tcpdump is a fast, efficient CLI tool to capture and filter network packets
    
-   It supports saving and reading `.pcap` files, which can be opened in GUI tools later
    
-   BPF syntax allows very flexible filtering with logical operators
    
-   Flags like `-nn`, `-c`, and `-s` help fine-tune what and how much data is captured
    
-   Tcpdump can display packet data in raw hex and ASCII for deep inspection
    
-   Great for scripting, automation, or working remotely via SSH
    
-   Useful in both real-time diagnostics and forensic investigations
