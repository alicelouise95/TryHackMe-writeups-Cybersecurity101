
### **TryHackMe: Cyber Security 101**

**Room:** `IDS Fundamentals`  
**Status:** Completed  
**Date:** 2025-08-31

----------

### **Goal**

To learn the fundamentals of Intrusion Detection Systems (IDS), their types, detection modes, and how tools like Snort can be used to detect malicious activities within a network.

---------

### **Key Topics Covered**



### 1. Understanding Intrusion Detection Systems (IDS)

An IDS is a security solution that detects malicious activities inside a network by monitoring incoming and outgoing traffic. It relies on two main detection approaches: signature-based and anomaly-based. When malicious or abnormal behavior is detected, an alert is generated for administrators. Importantly, an IDS only **notifies** about suspicious activity—it does not block it.

IDS solutions are categorized mainly by their deployment:

-   **Host Intrusion Detection System (HIDS):** Installed on individual machines, focusing on host-specific threats. Offers detailed host-level visibility but can be resource-heavy and difficult to manage in large networks.
    
-   **Network Intrusion Detection System (NIDS):** Operates at the network level, monitoring all traffic across hosts. Provides centralized insight into suspicious activities within the network.
    

### 2. IDS Detection Modes

-   **Signature-Based IDS:** Detects attacks by matching traffic patterns against a database of known signatures. Effective against previously identified threats, but cannot detect zero-day attacks since they lack stored signatures. Example: detecting a repeated attack that already exists in the IDS database.
    
-   **Anomaly-Based IDS:** Establishes a baseline of normal system or network behavior. Any deviations from this baseline are flagged as suspicious. Capable of detecting zero-day attacks but prone to false positives, since some normal activities may resemble malicious ones. False positives can be reduced through careful tuning of the baseline.
    
-   **Hybrid IDS:** Combines both approaches, leveraging signatures for known threats and anomaly detection for new ones. This provides broader protection and reduces limitations of either method alone.
    

### 3. Snort IDS

Snort is a widely used open-source IDS solution (developed in 1998) that supports both signature-based and anomaly-based detection. It relies on **rules** to detect traffic patterns, with pre-installed rule files as well as the ability to add or disable custom rules depending on requirements.

Snort operates in three modes:

-   **Packet Sniffer Mode:** Captures and displays packets without analysis. Useful for troubleshooting or monitoring traffic flow.
    
-   **Packet Logging Mode:** Logs network traffic into PCAP files for later forensic investigation, helping with root cause analysis of past attacks.
    
-   **Network Intrusion Detection System (NIDS) Mode:** The primary mode, applying rules in real-time to detect malicious traffic and generate alerts.
    

Snort’s configuration files and rule sets are stored under `/etc/snort`. The `snort.conf` file defines settings such as which rules to enable and which network ranges to monitor.

### 4. Snort Rules Structure

Snort rules follow a structured syntax that defines how traffic is detected and what action to take. For example:

    alert icmp any any -> $HOME_NET any (msg:"Ping Detected"; sid:1001; rev:1;)

-   **Action:** Defines what Snort does when the rule matches (e.g., `alert`).
    
-   **Protocol:** The network protocol being monitored (e.g., `ICMP`).
    
-   **Source IP & Port:** Define the traffic origin (e.g., `any`).
    
-   **Destination IP & Port:** Define where the traffic is going (e.g., `$HOME_NET`).
    
-   **Metadata:** Provides additional rule information:
    
    -   `msg`: Message displayed when triggered.
        
    -   `sid`: Unique signature ID.
        
    -   `rev`: Revision number, incremented when the rule changes.
        

Custom rules are typically saved in the `local.rules` file within `/etc/snort/rules`.

## What I Learned

-   IDS detects malicious activity but does not block it.
    
-   HIDS focuses on individual hosts; NIDS covers entire networks.
    
-   Signature-based IDS is effective for known threats but fails on zero-days.
    
-   Anomaly-based IDS can detect unknown threats but may generate false positives.
    
-   Hybrid IDS combines both approaches for stronger detection.
    
-   Snort can function in sniffer, logging, or full IDS modes.
    
-   Snort rules define traffic patterns and actions, with customization possible via `local.rules`.
