
### **TryHackMe: Cyber Security 101**

**Room:** `Burp Suite: The Basics`  
**Status:** Completed  
**Date:** 2025-08-13 

----------

### **Goal**

The main objective of this room was to introduce Burp Suite as a comprehensive tool for web application penetration testing. The room focused on familiarizing users with the Burp Suite interface, its core modules, interception and manipulation of HTTP/HTTPS requests, and basic practical testing techniques.

---------

### **Key Topics Covered**

**1. Overview of Burp Suite**

Burp Suite is a Java-based framework designed to serve as a comprehensive solution for web application penetration testing. It captures and enables manipulation of all HTTP/HTTPS traffic between a browser and a web server. By intercepting requests, users can route them to various components within the Burp Suite framework for detailed analysis.

-   **Editions**: Burp Suite is available in Community, Professional, and Enterprise editions.
    
    -   **Community Edition**: Free, includes essential tools like Proxy, Repeater, Intruder (with rate limitations), Decoder, Comparer, and Sequencer.
        
    -   **Professional/Enterprise**: Paid versions with advanced features, including automated scanning, project saving, and extended extension support.
        
-   **Extensions**: Burp Suite supports a wide range of third-party extensions through the BApp Store. Examples include Logger++, which enhances logging functionality. While some extensions require a professional license, many are available for the Community Edition.
    

----------

**2. Core Burp Suite Modules and Features**

-   **Proxy**: The primary feature of Burp Suite, allowing interception, inspection, and modification of requests and responses. Users can forward, drop, edit, or send captured traffic to other modules.
    
-   **Repeater**: Enables repeated sending of modified requests to a server. Useful for testing payloads, verifying input handling, and experimenting with vulnerabilities like SQL injection.
    
-   **Intruder**: Supports brute-force attacks, fuzzing, and endpoint testing. Limited in the Community Edition but still functional for basic testing.
    
-   **Decoder**: Allows encoding and decoding of captured data for analysis or safe payload crafting.
    
-   **Comparer**: Facilitates comparison of two pieces of data at the byte or word level.
    
-   **Sequencer**: Assesses the randomness of tokens such as session cookies, identifying potential weaknesses in token generation.
    
-   **Dashboard Quadrants**:
    
    -   **Tasks**: Defines background tasks executed by Burp Suite.
        
    -   **Event Log**: Tracks actions performed by the framework.
        
    -   **Issue Activity**: Displays vulnerabilities identified by automated scans (Professional only).
        
    -   **Advisory**: Provides detailed information, references, and remediation suggestions for identified vulnerabilities.
        

----------

**3. Navigation and Settings**

-   **Module Navigation**: The top menu bar lists all modules (Dashboard, Target, Proxy, Intruder, Repeater, etc.). Sub-tabs within each module contain module-specific options and settings. Tabs can also be detached for easier workflow management.
    
-   **Settings Types**:
    
    -   **Global Settings**: Apply to the entire Burp Suite installation.
        
    -   **Project Settings**: Apply only to the current project session. Community Edition does not support saving projects, so project-specific settings are lost upon exit.
        

----------

**4. Burp Proxy Configuration**

-   The Proxy intercepts requests between a browser and a target server. Traffic can be captured, modified, and forwarded to other tools or modules.
    
-   By default, server responses are not intercepted unless explicitly configured. Custom interception rules can provide flexibility.
    
-   Browsers must be configured to redirect traffic through Burp Suite, commonly using **FoxyProxy**, specifying the IP address and port.
    
-   **Intercept Function**: When enabled, requests hang until manually forwarded, allowing modification of input or testing payloads. Intercept should only be left on when deliberate interception is required, to avoid navigation issues.
    

----------

**5. Target Tab and Scoping**

-   **Site Map**: Displays the structure of a web application in a tree format. Every page visited through the proxy is automatically mapped, including API endpoints. Professional Edition supports automated crawling.
    
-   **Issue Definitions**: Contains a detailed list of common web vulnerabilities with descriptions and references.
    
-   **Scope Settings**: Define which domains or IPs are in scope, controlling what Burp Suite logs and manipulates. This helps avoid overwhelming data capture and ensures focus on specific targets.
    
-   **Built-in Chromium Browser**: Pre-configured to use Burp Proxy without additional modifications.
    
-   **Scoping Benefits**:
    
    -   Reduces clutter by focusing only on relevant traffic.
        
    -   Proxy can be set to ignore all out-of-scope requests entirely.
        

----------

**6. Example Attack Workflow**

-   Navigated to a THM-provided website's support page containing an email input and query form.
    
-   Burp Proxy intercept was enabled. Entered legitimate input for initial testing.
    
-   Captured request in the Proxy and modified the email field with a basic XSS payload:

    `<script>alert("Succ3ssful XSS")</script>`

-   URL-encoded the payload using Ctrl + U for safe transmission.
    
-   Forwarded the modified request to the server, demonstrating practical manipulation of intercepted traffic.
    

This exercise highlighted how Burp Suite can be used to test client-side validation bypass and input manipulation.

----------

### **What I Learned**

-   Burp Suite serves as a centralized framework for web application penetration testing.
    
-   Understanding core modules (Proxy, Repeater, Intruder, Decoder, Comparer, Sequencer) is essential for effective testing.
    
-   Proxy configuration and interception are critical for capturing and manipulating HTTP/HTTPS requests.
    
-   Proper scoping helps manage and focus testing, preventing unnecessary data capture.
    
-   Extensions from the BApp Store can enhance functionality, even in the Community Edition.
    
-   Practical exercises, like XSS testing, illustrate the application of Burp Suite tools in real-world scenarios.
