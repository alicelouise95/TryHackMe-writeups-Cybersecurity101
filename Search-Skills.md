
### **TryHackMe: Cyber Security 101**

**Room:** `Search Skills`  
**Status:** Completed  
**Date:** 2025-07-20

----------

### **Goal**

Learn how to effectively search for reliable information in cybersecurity, evaluate sources, and use specialized tools to discover technical vulnerabilities, exploits, and related information.

----------

### **Key Topics Covered**

**1. Evaluating Information Sources**

-   The internet allows anyone to publish content, but not all sources are credible.
    
-   When evaluating information, consider:
    
    -   **Source**: Who published it?
        
    -   **Evidence & Reasoning**: Are claims backed by data or logic?
        
    -   **Objectivity & Bias**: Is there an agenda or slant?
        
    -   **Corroboration**: Is the information confirmed elsewhere?
        
    -   **Consistency**: Does it align with known facts?
        
-   **Snake oil cryptography** refers to insecure or deceptive cryptographic products:
    
    -   **Secret systems**: Rely on undisclosed algorithms; this contradicts best practices that emphasize public scrutiny.
        
    -   **Technobabble**: Use of complex jargon to obscure lack of real security.
        

----------

**2. Search Engines and Search Operators**

-   **Popular Search Engines**: Google, Bing, DuckDuckGo
    
-   **Google Search Operators**:
    
    -   `"exact phrase"`: Search for an exact match
        
    -   `site:`: Restrict search to a specific domain
        
    -   `-`: Exclude a term
        
    -   `filetype:`: Search for specific file types
        

----------

**3. Specialized Search Engines**

-   **Shodan**:
    
    -   Search for internet-connected devices like servers, routers, and IoT.
        
    -   Example: Identify outdated server software versions globally.
        
-   **Censys**:
    
    -   Catalogs internet assets, domains, open ports, and certificates.
        
    -   Useful for asset discovery and network auditing.
        
-   **VirusTotal**:
    
    -   Upload and scan files/URLs using multiple antivirus engines.
        
    -   Check for malware or indicators of compromise.
        
-   **HaveIBeenPwned**:
    
    -   Enter an email to check if it appears in known data breaches.
        
    -   Helps assess account exposure and trigger remediation steps.
        

----------

**4. Vulnerabilities and Exploits**

-   **CVE (Common Vulnerabilities and Exposures)**:
    
    -   A standardized identifier system for known vulnerabilities.
        
    -   Each CVE has an ID and details regarding affected systems.
        
-   **Exploit Database**:
    
    -   A repository of public exploit code.
        
    -   Some exploits are verified and usable for red teaming and testing.
        
-   **GitHub**:
    
    -   Hosts tools, scripts, and exploit PoCs.
        
    -   Often includes community contributions related to CVEs and offensive security.
        

----------

**5. Reading Technical Documentation**

-   **Linux Manual Pages (man pages)**:
    
    -   Access with `man <command>` (e.g., `man ip`) for syntax and usage.
        
-   **Microsoft Docs**:
    
    -   Official technical documentation for Windows and other Microsoft products.
        
-   **Why Documentation Matters**:
    
    -   Official documentation is usually the most accurate and up-to-date source for product behavior, usage, and features.
        

----------

**6. Social Media and Information Discovery**

-   Social platforms can be sources of threat intel, trends, and tools.
    
-   **Best Practices**:
    
    -   Use temporary emails when exploring platforms.
        
    -   Avoid linking professional research to personal identity.
        
-   **Security Risks**:
    
    -   Oversharing can leak answers to security questions or personal data (e.g., birthplaces, schools).
        
    -   Attackers can use social data for phishing or account takeover.
        
-   **Staying Updated**:
    
    -   Follow trusted cybersecurity professionals, researchers, and organizations.
        
    -   Social media is a dynamic source for emerging vulnerabilities, tools, and discussions.
        

----------

### What I Learned

-   Source reliability is critical. Claims should be verified and well-supported.
    
-   Search engines can be used in advanced ways to pinpoint precise data.
    
-   Specialized engines like Shodan, Censys, and VirusTotal uncover important technical insights.
    
-   Understanding CVEs and using platforms like Exploit DB and GitHub helps assess and simulate vulnerabilities.
    
-   Official documentation provides authoritative product knowledge.
    
-   Social media is both a threat surface and a valuable research tool for cybersecurity professionals.
