
### **TryHackMe: Cyber Security 101**

**Room:** `Introduction to SIEM`  
**Status:** Completed  
**Date:** 2025-08-27

----------

### **Goal**

To understand how SIEM solutions provide visibility across networks by collecting, normalizing, and analyzing logs from multiple sources. The main objective is to learn how SIEM enables monitoring, correlation, investigation, and response to security events in a SOC environment.

---------

### **Key Topics Covered**
### 1. The Importance of Log Visibility

I began by noting that every device in a network generates logs whenever an activity is performed—such as visiting a website or connecting via SSH. Since each component in a network communicates with others or with the internet, there are many log sources producing different types of data.

I understood that manually reviewing logs on each device during an incident would be tedious and inefficient. This is why SIEM solutions are valuable: they centralize log collection, provide real-time analysis, and allow for incident response at scale.

Key SIEM features I recorded:

-   Real-time log ingestion
    
-   Alerting against abnormal activity
    
-   24/7 monitoring and visibility
    
-   Early threat detection
    
-   Data insights and visualization
    
-   Incident investigation capabilities
    

----------

### 2. Log Sources: Host-Centric vs. Network-Centric

I broke down log sources into two main categories:

-   **Host-Centric Log Sources**  
    These capture events occurring on or related to a host. Examples I wrote down include:
    
    -   File access by a user
        
    -   Authentication attempts
        
    -   Process execution activity
        
    -   Registry key modifications
        
    -   PowerShell execution
        
-   **Network-Centric Log Sources**  
    These capture communication-related events between hosts or with the internet. Examples I noted include:
    
    -   SSH connections
        
    -   FTP file access
        
    -   Web traffic
        
    -   VPN resource access
        
    -   Network file sharing activity
        

This distinction helped me understand that SIEM needs visibility on both the host and network sides for full coverage.

----------

### 3. Devices and Their Logs

I explored how different devices in a network generate and store logs:

-   **Windows Machines:**  
    Events recorded and viewed using the Event Viewer utility.
    
-   **Linux Workstations:**  
    Common log storage locations include:
    
    -   `/var/log/httpd` – HTTP request/response and error logs
        
    -   `/var/log/cron` – Cron job events
        
    -   `/var/log/auth.log` and `/var/log/secure` – Authentication-related logs
        
    -   `/var/log/kern` – Kernel events
        
-   **Web Servers:**  
    Apache logs typically stored in `/var/log/apache` or `/var/log/httpd`.
    

I recognized that these logs, when ingested into SIEM, provide rich data for security monitoring and investigation.

----------

### 4. Log Ingestion into SIEM

I recorded several methods SIEM solutions use to ingest logs:

1.  **Agent/Forwarder:** Lightweight tools installed on endpoints that capture logs and forward them to SIEM.
    
2.  **Syslog:** A widely used protocol for centralizing logs from servers, databases, and applications.
    
3.  **Manual Upload:** Offline log ingestion for quick analysis (e.g., Splunk, ELK).
    
4.  **Port-Forwarding:** Endpoints send data to SIEM on a listening port.
    

Once ingested, the logs are normalized for consistent analysis.

----------

### 5. SIEM in the SOC Ecosystem

I noted that SIEM is a critical component of a Security Operations Center (SOC). Its capabilities include:

-   Correlating events from different sources
    
-   Providing visibility into host and network activities
    
-   Investigating threats and enabling timely responses
    
-   Supporting proactive threat hunting beyond static rules
    

SOC Analysts use SIEM for:

-   Monitoring and investigating
    
-   Identifying false positives
    
-   Tuning noisy rules
    
-   Reporting and compliance
    
-   Covering blind spots in network visibility
    

----------

### 6. Dashboards in SIEM

I learned that dashboards are one of the most important parts of SIEM. They present normalized and ingested data as actionable insights. Dashboards can be default or custom-built, and they display information such as:

-   Alert highlights
    
-   System notifications
    
-   Health alerts
    
-   Failed login attempts
    
-   Ingested event counts
    
-   Triggered rules
    
-   Top domains visited
    

This makes dashboards the main interface where analysts spend most of their time monitoring activity.

----------

### 7. Correlation Rules and Alerts

SIEM uses correlation rules—logical expressions that trigger alerts when conditions are met. Examples I noted:

-   **Multiple Failed Login Attempts:** If a user has 5 failed logins in 10 seconds, raise an alert.
    
-   **Successful Login After Failed Attempts:** Raise an alert for potential brute-force success.
    
-   **USB Activity:** Raise an alert when a USB is plugged in (if restricted by policy).
    
-   **Outbound Traffic > 25MB:** Potential data exfiltration alert (threshold depends on company policy).
    

These rules ensure timely threat detection and help analysts take appropriate action.

----------

### 8. Analyst Workflow in SIEM

Once an alert is triggered, analysts review the associated events and rules to determine the outcome. From my notes, the possible actions are:

-   **False Alarm:** Requires rule tuning to reduce future false positives.
    
-   **True Positive:** Further investigation required.
    
-   **Contact Asset Owner:** Confirm details of suspicious activity.
    
-   **Suspicious Activity Confirmed:**
    
    -   Isolate the infected host
        
    -   Block suspicious IPs
        

This structured workflow ensures that alerts are properly triaged and acted upon.

----------

## What I Learned

-   Logs are generated by all network devices and provide critical visibility.
    
-   SIEM centralizes log ingestion, correlation, and monitoring.
    
-   Host-centric and network-centric logs together give full coverage.
    
-   Analysts rely heavily on dashboards for insights and alerts.
    
-   Correlation rules are key to detecting threats quickly.
    
-   Analyst workflow includes tuning rules, verifying alerts, and responding to incidents.
