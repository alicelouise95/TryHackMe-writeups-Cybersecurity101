
### **TryHackMe: Cyber Security 101**

**Room:** `JavaScript Essentials`  
**Status:** Completed  
**Date:** 2025-08-11

----------

### **Goal**

To understand the fundamental concepts and usage of JavaScript in web development, including variables, functions, control flow, script integration methods, and security best practices.

---------

### **Key Topics Covered**

**1. Introduction to JavaScript**

JavaScript (JS) is a widely-used scripting language that enables developers to add interactive elements to websites built with HTML and CSS. It allows for features such as form validation, clickable actions, animations, and dynamic content updates.

----------

**2. Variables and Data Types**

-   Variables act as containers for storing data values, referenced by unique names.
    
-   JS supports three ways to declare variables: `var`, `let`, and `const`.
    
    -   `var` is function scoped.
        
    -   `let` and `const` are block scoped, providing better control within code blocks.
        
-   Variables can hold various data types, including:
    
    -   String (text)
        
    -   Number (numeric values)
        
    -   Boolean (true/false)
        
    -   Null (intentional absence of value)
        
    -   Undefined (uninitialized variable)
        
    -   Object (complex data like arrays)
        

----------

**3. Functions**

Functions group code blocks designed to perform specific tasks. They can accept parameters (arguments) and can be reused multiple times. For example, a function to print a student’s exam result based on their roll number:

    function PrintResult(rollNum) {
        alert("Username with roll number " + rollNum + " has passed the exam");
    }
    for (let i = 0; i < 100; i++) {
        PrintResult(rollNumbers[i]);
    }

**4. Loops**

Loops run a block of code repeatedly while a condition remains true. Common types include:

-   `for`
    
-   `while`
    
-   `do...while`
    

Loops are useful for iterating over lists or repeating tasks.

--------

**5. Request-Response Cycle**

This is the process where a user’s browser (client) sends a request to a web server, and the server responds with the requested data such as a webpage or resources.

----
**6. Integrating JavaScript with HTML**

-   **Internal JavaScript:** Embedded directly within HTML files using `<script>` tags, either in the `<head>` or `<body>` sections.
    
    Example: 

    
        let x = 5;
        let y = 10;
        let result = x + y;
        document.getElementById("result").innerHTML = "The result is: " + result;
    
    -   **External JavaScript:** Stored in separate `.js` files linked to HTML via a `<script src="file.js"></script>` tag. This improves organization and maintainability.
    
----------

**7. JavaScript Dialog Boxes**

JS provides built-in dialog boxes for user interaction:

-   **alert:** Displays a message with an “OK” button.
    
    -   Example:
    
     `alert("Hello, Alice");`
        
-   **prompt:** Displays a dialog for user input; returns the input or null if cancelled.
    
    -   Example:

    `let name = prompt("What is your name?");
    alert("Hello " + name);`

-   **confirm:** Displays a message with “OK” and “Cancel” buttons; returns true or false.
    
    -   Example:

    `confirm("Are you sure?");`
        

Security consideration: Improper use can lead to vulnerabilities like cross-site scripting (XSS).

------

**8. Control Flow**

Defines the order of executing statements based on conditions using structures like:

-   `if-else`
    
-   `switch`
    
-   loops (`for`, `while`, `do...while`)
    

Example:


    age = prompt("What is your age");
    if (age >= 18) {
        document.getElementById("message").innerHTML = "You are an adult.";
    } else {
        document.getElementById("message").innerHTML = "You are a minor.";
    }

**9. Minification and Obfuscation**

-   **Minification:** Compresses JS files by removing whitespace, comments, and shortening variable names to reduce file size and improve load times.
    
-   **Obfuscation:** Makes code harder to understand by renaming variables/functions to meaningless names and adding dummy code, increasing difficulty for attackers to reverse engineer.
    

----------

**10. Best Practices for Secure and Efficient JavaScript**

-   Avoid relying solely on client-side validation since users can disable or manipulate JS.
    
-   Do not include untrusted third-party libraries to prevent introducing malicious code.
    
-   Never hardcode sensitive data (e.g., API keys, credentials) in client-side code as it can be accessed through the source.
    
-   Minify and obfuscate JS code in production to improve performance and complicate reverse engineering by attackers.
    

----------

### **What I Learned**

-   JavaScript is essential for adding interactivity and dynamic content to websites.
    
-   Variables in JS can be declared with `var`, `let`, and `const`, each with different scope rules.
    
-   Functions encapsulate reusable code blocks, accepting parameters and executing tasks.
    
-   Control flow structures manage the execution path based on conditions.
    
-   JS can be integrated internally within HTML or externally via separate `.js` files.
    
-   Built-in dialog boxes (`alert`, `prompt`, `confirm`) enable user interaction but must be used securely.
    
-   Minification and obfuscation help optimize and protect JavaScript code.
    
-   Security best practices include avoiding client-only validation, untrusted libraries, and exposing sensitive data in code.
