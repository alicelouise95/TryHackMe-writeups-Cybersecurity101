
### **TryHackMe: Cyber Security 101**

**Room:** `Gobuster: The Basics`  
**Status:** Completed  
**Date:** 2025-08-17 

----------

### **Goal**

To understand how to use Gobuster, an open-source enumeration tool, to brute force and discover hidden web directories, files, DNS subdomains, and virtual hosts. The exercises focused on learning how to use Gobuster’s different modes, interpret its results, and apply its command-line flags effectively.

---------

### **Key Topics Covered**


### 1. Enumeration and Brute Force

-   **Enumeration** was defined as the process of listing all available resources, regardless of whether or not they are accessible.
    
-   **Brute Force** was described as the process of trying every possibility until a match is found.
    
-   Gobuster applies brute force through wordlists, appending possible paths or hostnames to a given domain or IP, and then checking for valid responses.
    

This provided the foundational context for why Gobuster is useful in penetration testing, bug bounty hunting, and security assessments.

----------

### 2. General Gobuster Flags

Running `gobuster --help` revealed several important flags that shape how Gobuster operates:

-   **-t / --threads:** Sets the number of threads for concurrent requests. The default is 10, but larger wordlists may require adjusting this number based on system resources.
    
-   **-w / --wordlist:** Defines the wordlist Gobuster will iterate through, appending entries to the base URL.
    
-   **--delay:** Adds time between requests to evade detection mechanisms and mimic normal traffic.
    
-   **--debug:** Useful for troubleshooting errors.
    
-   **--output:** Saves enumeration results into a file.
    

----------

### 3. Directory Enumeration (dir mode)

-   **Purpose:** Gobuster’s `dir` mode enumerates directories and files on a web server. This is useful for penetration testing because many web applications follow predictable structures.
    

Flags from `gobuster dir --help` included:

-   **-c / --cookies:** Pass a cookie with each request.
    
-   **--e / --extensions:** Scan for files with specified extensions (e.g., `.php`, `.js`).
    
-   **-H / --headers:** Pass custom headers with requests.
    
-   **-k / --no-tls-validation:** Skips TLS certificate validation, often useful in CTFs where self-signed certificates cause errors.
    
-   **-n / --no-status:** Hides response status codes for cleaner output.
    
-   **-P / --password** and **-U / --username:** Used together for authenticated requests.
    
-   **-s / --status-codes:** Display only specified status codes (e.g., `200` or ranges like `300-400`).
    
-   **-b / --status-codes-blacklist:** Hide specified status codes from results.
    
-   **-r / --followredirect:** Follows HTTP redirects.

**Example command:**

`gobuster dir -u "http://www.example.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x .php,.js`

This command sets Gobuster to directory and file enumeration mode, defines the target URL, applies a specific wordlist, and checks for files with `.php` and `.js` extensions.

----------

### 4. DNS Subdomain Enumeration (dns mode)

-   **Purpose:** Gobuster’s `dns` mode brute forces subdomains of a target domain. This is important because vulnerabilities might exist in subdomains even if the main domain is patched.
    

Flags from `gobuster dns --help`:

-   **-c / --show-cname:** Displays CNAME records.
    
-   **-i / --show-ips:** Shows IP addresses for domains/subdomains.
    
-   **-r / --resolver:** Use a custom DNS server.
    
-   **-d / --domain:** Defines the target domain.

**Example command:**

    gobuster dns -d example.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt

This command uses `dns` mode to attempt subdomain discovery by combining the base domain with entries from the chosen wordlist.

### 5. Virtual Host Enumeration (vhost mode)

-   **Purpose:** Gobuster’s `vhost` mode brute forces virtual hosts. Unlike subdomains (which exist in DNS), virtual hosts are multiple websites hosted on the same server IP.
    

Key distinctions noted:

-   **vhost mode:** Navigates to URLs created by combining the hostname with wordlist entries.
    
-   **dns mode:** Performs DNS lookups on FQDNs created with wordlist entries.
    

Flags from `gobuster vhost --help`:

-   **-u / --url:** Sets the base URL.
    
-   **--append-domain:** Appends the base domain to wordlist entries.
    
-   **-m / --method:** Sets the HTTP method (e.g., GET, POST).
    
-   **--domain:** Appends a domain to each wordlist entry.
    
-   **--exclude-length:** Filters results by excluding certain response body lengths.
    
-   **-r / --follow-redirect:** Follows HTTP redirects.
    

**Example command:**

    gobuster vhost -u "http://example.thm" -w /path/to/wordlist

This command launches vhost enumeration against the target domain using the provided wordlist.

----------

## What I Learned

-   Enumeration systematically lists resources, while brute force tests every possibility until a match is found.
    
-   Gobuster is highly flexible, with flags to manage performance, stealth, and output.
    
-   `dir` mode is useful for finding hidden directories and files by combining URLs with wordlists and extensions.
    
-   `dns` mode discovers subdomains, which may expose overlooked vulnerabilities.
    
-   `vhost` mode reveals hidden virtual hosts hosted on the same server.
