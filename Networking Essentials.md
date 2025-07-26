
### **TryHackMe: Cyber Security 101**

**Room:** `Networking Essentials`  
**Status:** Completed  
**Date:** 2025-07-26

----------

### **Goal**

Gain a solid foundation in essential networking concepts such as DHCP, ARP, ICMP, routing protocols, and NAT, understanding how devices communicate, how IP addresses are assigned, how routes are determined, and how internal networks access the internet.

----------


### **Key Topics Covered**



**1. DHCP (Dynamic Host Configuration Protocol)**

DHCP automates the network configuration process by assigning:

-   IP address
    
-   Subnet mask
    
-   Gateway
    
-   DNS server
    

**Why it matters:**

-   Saves time and effort for mobile devices.
    
-   Prevents IP conflicts.
    
-   Enables dynamic adaptation when connecting to new networks.
    

**Protocol Details:**

-   Application-layer protocol using **UDP**
    
-   Server listens on **UDP port 67**, clients send from **UDP port 68**
    

**DORA Process:**

-   **Discover** – Client broadcasts to locate a DHCP server
    
-   **Offer** – Server replies with a possible IP and config
    
-   **Request** – Client accepts the offer
    
-   **Acknowledge** – Server confirms assignment (IP is leased)
    

**At the end of the process, the device receives:**

-   A leased IP
    
-   Gateway to route traffic
    
-   DNS server for domain name resolution
    

----------

**2. ARP (Address Resolution Protocol)**

ARP resolves IP addresses to MAC addresses, allowing communication within a local network.

**Example:**

-   Host `192.168.66.89` wants to contact `192.168.66.1`
    
-   Sends **ARP Request** (broadcast MAC `ff:ff:ff:ff:ff:ff`)
    
-   Gets **ARP Reply** with the target's MAC address
    
-   Devices can now exchange data link layer frames
    

**Layer:** Operates at **Layer 2** (Data Link), though it bridges to **Layer 3** (IP).

----------

**3. ICMP (Internet Control Message Protocol)**

Used primarily for diagnostics and error reporting.

**Tools:**

-   **Ping** – Sends ICMP Echo Request to test reachability
    
-   **Traceroute** – Reveals the path packets take to a destination
    

**Ping Functionality:**

-   Measures round-trip time
    
-   Confirms whether a target is reachable
    

----------

**4. Routing Protocols**

Routing determines how data moves between devices across networks. These protocols decide the most efficient path.

**Types of Routing Protocols:**

-   **OSPF** – Open Shortest Path First
    
    -   Link-state protocol
        
    -   Routers share a map of the network topology
        
    -   Finds shortest path using full network knowledge
        
-   **EIGRP** – Enhanced Interior Gateway Routing Protocol
    
    -   Cisco proprietary
        
    -   Combines link-state and distance-vector elements
        
    -   Routes based on cost metrics like bandwidth/delay
        
-   **BGP** – Border Gateway Protocol
    
    -   Used between Internet Service Providers
        
    -   Routes data across different autonomous systems (AS)
        
    -   Ensures global routing across the Internet
        
-   **RIP** – Routing Information Protocol
    
    -   Simple distance-vector protocol
        
    -   Selects routes based on **hop count**
        
    -   Best for small networks
        

----------

**5. NAT (Network Address Translation)**

NAT allows multiple internal (private) IP addresses to share a single public IP for internet access.

**Why it matters:**

-   Conserves public IP addresses
    
-   Provides a layer of security
    
-   Allows internal devices to access the internet without being directly exposed
    

**How it works:**

-   The NAT-enabled router maintains a **translation table**
    
-   Maps internal private IPs to a single external public IP
    
-   Tracks each connection to ensure proper routing
    

----------

### **What I Learned**

-   Understood how devices get IP addresses automatically via DHCP
    
-   Learned how MAC addresses are discovered using ARP for local communication
    
-   Practiced using ICMP through tools like `ping` and `traceroute`
    
-   Gained a solid overview of major routing protocols and their differences
    
-   Discovered how NAT enables multiple devices to share one public IP securely
    
-   Developed a deeper appreciation for the layers of abstraction that make network communication possible
    

----------
