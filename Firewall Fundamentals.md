
### **TryHackMe: Cyber Security 101**

**Room:** `Firewall Fundamentals`  
**Status:** Completed  
**Date:** 2025-08-29

----------

### **Goal**

To understand the fundamentals of firewalls, including their types, functionalities, rule components, and practical configuration on Windows and Linux systems.

---------

### **Key Topics Covered**


### 1. Introduction to Firewalls

Firewalls inspect incoming and outgoing network traffic on devices or networks, applying predefined rules to allow or deny traffic. They act as gatekeepers, controlling what passes through based on these rules. Modern firewalls go beyond basic rule-based filtering, providing advanced functionalities to detect and block threats.

The deployment of firewalls became widespread as organizations realized their ability to filter harmful traffic effectively. Firewalls can operate at different layers of the OSI model, and each type serves a unique purpose.

----------

### 2. Types of Firewalls

-   **Stateless Firewalls**  
    Operate at OSI layers 3 (Network) and 4 (Transport). They filter packets based solely on rules, without tracking the state of previous connections. While efficient and fast, they cannot make decisions based on past traffic patterns, meaning future packets from the same source are treated independently.
    
-   **Stateful Firewalls**  
    Track previous connections in a **state table**, allowing them to make decisions based on the history of a connection. For example, if some packets from a source are allowed, all subsequent packets in that connection may be permitted automatically. This adds security while monitoring traffic patterns.
    
-   **Proxy Firewalls (Application-Level Gateways)**  
    Operate at OSI layer 7, inspecting the contents of packets. They act as intermediaries between the internal network and the internet, providing anonymity for internal IP addresses. They allow content filtering and application control, and can decrypt SSL/TLS traffic for inspection.
    
-   **Next-Generation Firewalls (NGFW)**  
    Operate across layers 3–7, offering **deep packet inspection**, intrusion prevention, and heuristic analysis for detecting anomalies. They can decrypt SSL/TLS traffic and correlate data with threat intelligence feeds for real-time protection.
    

**Key characteristics of firewall types:**

-   Stateless firewalls: Basic filtering, no tracking of previous connections, efficient for high-speed networks.
    
-   Stateful firewalls: Monitor network connections, apply complex rules, recognize traffic patterns.
    
-   Proxy firewalls: Inspect packet contents, provide content filtering and application control, SSL/TLS inspection.
    
-   Next-generation firewalls: Advanced threat protection, intrusion prevention, heuristic analysis, SSL/TLS inspection.
    

----------

### 3. Firewall Rules Components

Rules define how firewalls manage traffic. Key components include:

-   **Source Address:** IP origin of the traffic
    
-   **Destination Address:** IP target of the traffic
    
-   **Port:** Port number used for the connection
    
-   **Protocol:** Communication protocol (e.g., TCP, UDP)
    
-   **Action:** Defines whether traffic is allowed, denied, or forwarded
    
-   **Direction:** Inbound or outbound traffic
    

**Actions Examples:**

-   **Allow:** Permits traffic that matches the rule.
    
-   **Deny:** Blocks traffic, reducing potential attack surfaces.
    
-   **Forward:** Redirects traffic to another network segment, useful for routing purposes.
    

**Rule Categories:**

-   **Inbound Rules:** Apply to incoming traffic.
    
-   **Outbound Rules:** Apply to outgoing traffic.
    
-   **Forwarding Rules:** Redirect traffic within the network.
    

----------

### 4. Firewalls on Windows

**Windows Defender Firewall** is built into Windows OS and provides basic and advanced firewall functionalities. It uses **network profiles** determined by Network Location Awareness (NLA):

-   **Private Networks:** Home or trusted networks
    
-   **Guest/Public Networks:** Public or untrusted networks
    

Users can allow or block applications via the "Allow an app or feature" option, or create custom rules for specific ports and protocols.

**Custom Rule Example (Block Outgoing Traffic on Ports 80 & 443):**

1.  Open **Advanced Settings** → Outbound Rules → New Rule → Custom
    
2.  Select **All Programs**, choose **TCP**, set Remote Port to 80,443 → Next
    
3.  Action: **Block the Connection** → Next
    
4.  Profile: Keep all network profiles selected → Name and finish rule
    

----------

### 5. Firewalls on Linux

Linux uses the **Netfilter framework**, which provides packet filtering, NAT, and connection tracking. Various firewall utilities leverage this framework:

-   **iptables:** Widely used, provides core firewall functionalities
    
-   **nftables:** Successor to iptables with enhanced capabilities
    
-   **firewalld:** Comes with predefined zones and rules
    
-   **ufw (Uncomplicated Firewall):** Simplifies rule creation for ease of use
    

**Practical Commands with UFW:**

-   `sudo ufw status` – Check firewall status
    
-   `sudo ufw enable` / `sudo ufw disable` – Enable or disable firewall
    
-   `sudo ufw default allow outgoing` – Allow all outgoing traffic by default
    
-   `sudo ufw deny 22/tcp` – Block incoming traffic on port 22
    
-   `sudo ufw status numbered` – List active rules with numbers
    
-   `sudo ufw delete <number>` – Remove a rule by number
    

----------

## What I Learned

-   Firewalls control traffic based on predefined rules and can be stateless, stateful, proxy, or next-generation.
    
-   Rule components include source, destination, port, protocol, action, and direction.
    
-   Actions include Allow, Deny, and Forward, applied through inbound, outbound, or forwarding rules.
    
-   Windows Defender Firewall allows configuration by network profile, custom rules, and application control.
    
-   Linux firewalls utilize Netfilter through utilities such as iptables, nftables, firewalld, and ufw for packet filtering and traffic control.
