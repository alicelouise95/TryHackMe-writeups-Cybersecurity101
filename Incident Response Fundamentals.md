

### **TryHackMe: Cyber Security 101**

**Room:** `Incident Response Fundamentals`  
**Status:** Completed  
**Date:** 2025-08-24

----------

### **Goal**

To learn the fundamentals of incident response, including identifying incidents, assigning severity, following structured frameworks, and applying tools and playbooks to contain, eradicate, and recover from security incidents.

---------

### **Key Topics Covered**


### 1. Events, Alerts, and Incidents

Computing devices continuously generate events from interactive and non-interactive processes. These events are produced in massive numbers, making it difficult to manually spot malicious activity. Security solutions analyze these events and trigger **alerts** when suspicious patterns appear.

-   **False Positives** – Alerts that appear harmful but are ultimately benign. For example, a backup transferring data to a cloud service may resemble data exfiltration but is not malicious.
    
-   **True Positives** – Alerts confirmed as malicious, such as phishing attempts where attackers send fraudulent emails to compromise systems.
    

True positives are referred to as **incidents**, and once identified, they are assigned a severity level (critical, high, medium, or low).

----------

### 2. Types of Security Incidents

Several categories of incidents were identified in my notes:

-   **Malware Infections** – Malicious software spread through files (executables, documents, text files) with the potential to harm systems, networks, or applications.
    
-   **Security Breaches** – Unauthorized access to confidential data, threatening the integrity and confidentiality of an organization’s information.
    
-   **Data Leaks** – Exposure of sensitive information, either accidental (misconfigurations, human error) or intentional, often leading to reputational or financial damage.
    
-   **Insider Attacks** – Malicious actions carried out by individuals within the organization, such as a disgruntled employee using a USB to spread malware.
    
-   **Denial of Service (DoS) Attacks** – Flooding a system or network with illegitimate requests, exhausting resources, and preventing access for legitimate users.
    

Each incident’s impact is context-dependent: what may be minor for one organization could be catastrophic for another.

----------

### 3. Incident Response Frameworks

Incident response frameworks provide structured processes for handling incidents.

-   **SANS PICERL Framework (6 Phases):**
    
    1.  **Preparation** – Build resources, teams, and response plans.
        
    2.  **Identification** – Detect and confirm abnormal behaviors.
        
    3.  **Containment** – Minimize the attack’s impact (e.g., isolate machines, disable accounts).
        
    4.  **Eradication** – Remove threats to ensure a clean environment.
        
    5.  **Recovery** – Restore systems from backups or rebuild and test them.
        
    6.  **Lessons Learned** – Document gaps and improvements for future incidents.
        
-   **NIST Framework (4 Parts):**
    
    1.  Preparation
        
    2.  Detection & Analysis
        
    3.  Containment, Eradication, & Recovery
        
    4.  Post-Incident Activity
        

Organizations often adapt their own processes from these frameworks, recording them in an **Incident Response Plan (IRP)**. This plan is formally approved by management and outlines:

-   Roles and responsibilities
    
-   Incident response methodology
    
-   Communication with stakeholders and law enforcement
    
-   Escalation paths
    

----------

### 4. Security Solutions for Incident Detection

Because manual detection is impractical, organizations rely on specialized security solutions:

-   **SIEM (Security Information and Event Management):** Centralizes and correlates logs to identify incidents.
    
-   **AV (Antivirus):** Detects known malware and performs system scans.
    
-   **EDR (Endpoint Detection and Response):** Deployed on endpoints to detect advanced threats, with capabilities to contain and eradicate them.
    

These tools complement one another, ensuring coverage from known malware to more sophisticated attacks.

----------

### 5. Playbooks for Incident Response

**Playbooks** are structured sets of instructions guiding the investigation and response to specific incidents. They ensure consistency, thoroughness, and rapid action.

**Example: Phishing Email Playbook**

1.  Notify stakeholders about the phishing incident.
    
2.  Analyze the email header and body for malicious indicators.
    
3.  Check for and analyze attachments.
    
4.  Determine if any attachments were opened.
    
5.  Isolate compromised systems from the network.
    
6.  Block the sender to prevent further attempts.
    

This structured approach ensures that even complex incidents are managed systematically.

----------

## What I Learned

-   Events and alerts must be carefully analyzed to separate false positives from true incidents.
    
-   Incidents include malware infections, breaches, leaks, insider threats, and DoS attacks.
    
-   Severity and impact of incidents vary depending on organizational context.
    
-   The **SANS PICERL** and **NIST** frameworks provide structured processes for incident response.
    
-   An **Incident Response Plan** formalizes roles, methodologies, communication, and escalation.
    
-   Security solutions like **SIEM, AV, and EDR** play critical roles in incident detection.
    
-   **Playbooks** provide clear, step-by-step guidance for handling specific incident types, such as phishing.
