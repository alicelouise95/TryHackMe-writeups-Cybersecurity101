
### **TryHackMe: Cyber Security 101**

**Room:** `Linux Shells`  
**Status:** Completed  
**Date:** 2025-07-24

----------

### **Goal**

Gain familiarity with Linux shell environments and their capabilities, including common commands, different shell types, shell scripting fundamentals, and hands-on editing and execution of scripts to automate tasks.

----------


### **Key Topics Covered**

**1. Basic Shell Commands**  
These were reviewed but already familiar:

-   `cd` – Change directory
    
-   `pwd` – Print working directory
    
-   `whoami` – Show current user
    
-   `ls` – List directory contents
    
-   `cat` – Display file contents
    
-   `grep` – Search for patterns in text
    

----------

**2. Linux Shell Types**

-   Use `echo $SHELL` to check the current shell.
    
-   Use `cat /etc/shells` to list available shells.
    
-   To switch temporarily, type the name of a shell (e.g., `zsh`).
    
-   To switch permanently, use `chsh -s /usr/bin/zsh` (requires credentials).
    

**Shell Comparison Highlights:**

-   **Bash** (Bourne Again Shell):
    
    -   Default for most distros
        
    -   Powerful scripting
        
    -   Tab completion
        
    -   Command history (`history`)
        
-   **Z Shell (zsh):**
    
    -   Modern shell with scripting, history, and advanced tab completion
        
    -   Auto spell-correction
        
    -   Highly customizable
        
-   **Fish (Friendly Interactive Shell):**
    
    -   Beginner-friendly syntax
        
    -   Auto-corrects commands
        
    -   Supports prompt customization, history, scripting, and tab completion
        

----------

**3. Shell Scripting & Components**

A shell script is a set of sequential commands stored in a file, ideal for automating tasks.

-   **Interpreter Declaration (Shebang):**  
    Start each script with `#!/bin/bash` to define the shell used.
    
-   **Giving Execute Permissions:**  
    `chmod +x scriptname.sh`
    
-   **Running the Script:**  
    `./scriptname.sh`
    

**Example Scripts Created:**

-    **User Input Script**  

    #!/bin/bash
    echo "Hey, what’s your name?"
    read name
    echo "Welcome, $name"

-    **Loop Script**  

    #!/bin/bash
    for i in {1..10};
	do
	  echo $i
	done

 -   **Conditional Script**
 

    #!/bin/bash
    echo "Please enter your name first:"
    read name
    if [ "$name" = "Stewart" ]; then
      echo "Welcome Stewart! Here is the secret: THM_Script"
    else
      echo "Sorry! You are not authorized to access the secret."
    fi

 -   **Multi-Function Script**
 
    #!/bin/bash
    username=""
    companyname=""
    pin=""
    for i in {1..3}; do
      if [ "$i" -eq 1 ]; then
        echo "Enter your Username:"
        read username
      elif [ "$i" -eq 2 ]; then
        echo "Enter your Company name:"
        read companyname
      else
        echo "Enter your PIN:"
        read pin
      fi
    done
    
    if [ "$username" = "John" ] && [ "$companyname" = "Tryhackme" ] && [ "$pin" = "7385" ]; then
      echo "Authentication Successful. You can now access your locker, John."
    else
      echo "Authentication Denied!!"
    fi

----------

**4. Practical Scripting Challenge**

Challenge: Locate the keyword thm-flag01-script hidden within .log files located in the /var/log directory on an Ubuntu machine.
A script, placed in the /home/user directory, requires modification by filling in missing values for the keyword and directory path. 
Running this corrected script as the root user will reveal which file contains the keyword. Additionally, the discovered file holds the answer to where the cat is sleeping.

My steps:

-   Located the script `flag_hunt.sh`.
    
-   Used `sudo su` to elevate privileges.
    
-   Edited the script with `nano`, inserting the line:  
    `"Flag: thm-flag01-script"`  
    and referenced `/var/log` for file output.
   - Ran the script, which gave the output `authentication.log`
   - Then navigated to the appropriate directory and used cat to retrieve the contents of the .log file:
   
    `cd /var/log`
	`cat authentication.log`
- Final output revealed the message:  
**“the cat is sleeping under the table”**

----------

### **What I Learned**

-   Reinforced understanding of essential Linux commands and shell environment configuration.
    
-   Gained practical experience in writing and executing shell scripts using loops, conditionals, and variables.
    
-   Learned how to inspect and modify existing scripts for real-world output.
    
-   Gained confidence in navigating the file system, changing shells, and performing privileged operations using `sudo`.
    
-   Discovered the flexibility and power of scripting for task automation and information retrieval in Linux.








