
### **TryHackMe: Cyber Security 101**

**Room:** `Logs Fundamentals`  
**Status:** Completed  
**Date:** 2025-08-25

----------

### **Goal**

To understand the purpose, types, and usage of logs in security, system monitoring, and troubleshooting. The main goal is to learn how logs act as digital footprints of system and user activity, and how they can be used for detection, investigation, and performance monitoring.

---------

### **Key Topics Covered**

### 1. Use Cases of Logs

Logs are essential for multiple operational and security-related purposes. Based on my notes, I explored the following use cases in detail:

-   **Security Events Monitoring:**  
    Logs help detect unusual behavior in real time. By monitoring logs continuously, it's possible to identify anomalies that could indicate an attack or misconfiguration.
    
-   **Incident Investigation and Forensics:**  
    Logs contain traces of all kinds of activities, including those that occurred during an incident. I noted that logs help security teams reconstruct events, perform root cause analysis, and understand the full scope of an attack.
    
-   **Troubleshooting:**  
    Logs often record errors in systems or applications. These entries are useful for diagnosing issues. I understood that reviewing logs during system failures helps in identifying what went wrong and how to fix it.
    
-   **Performance Monitoring:**  
    Logs provide performance-related data such as system load, application response times, or failure rates. I recorded that these logs are helpful for identifying performance bottlenecks or trends over time.
    
-   **Auditing and Compliance:**  
    Logs create an activity trail that is critical for auditing. I recognized that logs help demonstrate compliance with policies or regulations, especially in environments where accountability and traceability are required.
    

----------

### 2. Types of Logs

Logs are categorized based on the type of information they provide. I took detailed notes on each category:

-   **System Logs:**  
    These logs record core OS-level activities. I noted examples like:
    
    -   Startup/shutdown events
        
    -   Driver loading events
        
    -   System errors
        
    -   Hardware-related events  
        These logs are useful for diagnosing issues in the operating system.
        
-   **Security Logs:**  
    Security logs focus on events like:
    
    -   Authentication attempts
        
    -   Authorization changes
        
    -   Policy modifications
        
    -   User account changes or suspicious behavior  
        These are critical for detecting attacks or unauthorized activity.
        
-   **Application Logs:**  
    These track activity within specific applications, such as:
    
    -   User interactions
        
    -   Updates or modifications
        
    -   Application errors  
        These logs help in debugging application issues and monitoring user actions.
        
-   **Audit Logs:**  
    Audit logs are especially relevant for compliance and monitoring:
    
    -   Data access events
        
    -   System configuration changes
        
    -   User activity
        
    -   Policy enforcement  
        These logs ensure accountability and traceability of sensitive operations.
        
-   **Network Logs:**  
    These logs track network traffic:
    
    -   Incoming/outgoing traffic data
        
    -   Network-related issues  
        They assist in network troubleshooting and identifying malicious communication.
        
-   **Access Logs:**  
    These record access to resources:
    
    -   Web server logs
        
    -   Database access logs
        
    -   Application and API access logs  
        I understood that these are useful for identifying who accessed what and when.
        

----------

### 3. Log Analysis

I learned that **log analysis** involves reviewing logs to extract valuable information. The key purpose is to identify unusual or suspicious activity. I also noted that this process is essential in both proactive security monitoring and reactive incident response.

----------

### 4. Windows OS Logs and Event Viewer

Windows OS logs many activities across different categories. I recorded the following key log files:

-   **Application:** Logs related to application errors, warnings, or compatibility issues.
    
-   **System:** Logs related to OS-level events such as driver or hardware issues.
    
-   **Security:** Logs related to authentication, user changes, and security policies.
    

Windows provides a **GUI tool called Event Viewer** to inspect logs. Key fields include:

-   **Description:** Detailed activity information
    
-   **Log Name:** Indicates which log file it belongs to
    
-   **Logged:** Timestamp of the event
    
-   **Event ID:** A unique number assigned to specific events
    

I specifically noted the following **Event IDs** and their meanings:

-   **4624** – A user account successfully logged in
    
-   **4625** – A user account failed to log in
    
-   **4634** – A user account logged off
    
-   **4720** – A user account was created
    
-   **4724** – An attempt was made to reset a password
    
-   **4722** – A user account was enabled
    
-   **4725** – A user account was disabled
    
-   **4726** – A user account was deleted

### 5. Web Server Logs

Web servers log every request made to a website. For example, Apache stores logs in `/var/log/apache2/access.log`. I noted that these logs are often **rotated** into separate files by date or size.

Key fields I recorded:

-   **IP Address:** Identifies the user making the request.
    
-   **Timestamp:** Date and time of the request.
    
-   **Request:** Contains:
    
    -   **HTTP Method** (e.g., GET, POST)
        
    -   **URL** (the resource being accessed)
        
-   **Status Code:** Server’s response (e.g., 200, 404, 500)
    
-   **User-Agent:** Browser and OS information of the user
    

These fields help understand user behavior and identify suspicious requests or attacks.

----------

### 6. Linux Command-Line Utilities for Log Analysis

I took notes on several Linux tools useful for analyzing logs:

-   **cat**
    
    -   **Purpose:** Display the full contents of a log file.
        
    -   **Usage:** `cat access.log`
        
    -   **Advanced Use:** Combine logs into one file.  
        Example: `cat access1.log access2.log > combined_access.log`
        
-   **grep**
    
    -   **Purpose:** Search for a specific string or pattern in logs.
        
    -   **Usage:** `grep "192.168.1.1" access.log`
        
    -   **Result:** Shows all lines containing the IP.
        
-   **less**
    
    -   **Purpose:** View logs one page at a time, helpful for large files.
        
    -   **Usage:** `less access.log`
        
    -   **Navigation:**
        
        -   Spacebar: Move forward
            
        -   `b`: Move backward
            
    -   **Searching:**
        
        -   `/pattern`: Search for a pattern (e.g., `/404`)
            
        -   `n`: Go to the next match
            
        -   `N`: Go to the previous match
            

These tools were useful in practicing real-world log analysis in Linux.

----------

## What I Learned

-   Logs are essential for monitoring, investigating, and troubleshooting.
    
-   There are different types of logs (system, security, application, etc.), each serving a specific purpose.
    
-   Log analysis helps identify unusual activity and detect security incidents.
    
-   Windows Event Viewer provides a GUI for inspecting logs with helpful fields and event IDs.
    
-   Web server logs track detailed access data useful for investigation.
    
-   Linux utilities like `cat`, `grep`, and `less` are powerful tools for analyzing logs from the command line.
