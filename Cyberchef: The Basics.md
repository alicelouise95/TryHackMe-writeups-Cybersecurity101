
### **TryHackMe: Cyber Security 101**

**Room:** `CyberChef: The Basics`  
**Status:** Completed  
**Date:** 2025-09-04

----------

### **Goal**

Learn how to use CyberChef, a web-based tool for performing various data transformations and cryptographic operations, by understanding its interface, features, and practical workflow.

---------

### **Key Topics Covered**


1.  **Overview of CyberChef**  
    CyberChef is a simple and intuitive web-based application designed to perform a wide range of “cyber” operations directly in the browser. It can handle both basic tasks, like encoding/decoding (e.g., Base64, ROT13, Morse Code), and more advanced cryptographic operations, such as AES encryption or RSA decryption. Operations are applied using “recipes,” which are sequences of tasks executed in a specific order.
    
2.  **CyberChef Interface Areas**  
    CyberChef consists of four main areas, each with specific features:
    
    -   **Operations Area**:  
        This is a repository of all operations CyberChef can perform, neatly categorized for easy navigation. Users can search for specific operations to save time. Examples include:
        
        -   _From Morse Code_: Converts Morse Code into uppercase alphanumeric characters.
            
        -   _URL Encode_: Encodes special characters into percent-encoding for URLs.
            
        -   _To Base64_: Encodes raw data as an ASCII Base64 string.
            
        -   _To Hex_: Converts a string into hexadecimal bytes.
            
        -   _To Decimal_: Converts data into an array of ordinal integers.
            
        -   _ROT13_: A simple Caesar cipher rotating letters by 13 positions.
            
    -   **Recipe Area**:  
        Considered the heart of CyberChef, this area allows users to select, arrange, and fine-tune operations. Users can drag operations into the recipe, configure their options, and save or load recipes for repeated use. The “BAKE!” button executes the recipe on the input data.
        
    -   **Input Area**:  
        Users can paste, type, or drag files into this area. Additional features include:
        
        -   Adding new input tabs
            
        -   Uploading entire folders or single files
            
        -   Clearing input/output
            
        -   Resetting the pane layout
            
    -   **Output Area**:  
        The output area displays the result of processed data. Features include saving results to a file, copying raw output to the clipboard, replacing input with output, and maximizing the output pane for better visibility.
        
3.  **Approach to Using CyberChef**  
    A structured four-step process helps maximize efficiency:
    
    1.  Set a clear objective (e.g., decode a gibberish string to find a hidden message).
        
    2.  Input the data into CyberChef by pasting or uploading.
        
    3.  Select and apply relevant operations based on the data type and goal (e.g., ROT13, Base64).
        
    4.  Review the output and iterate if necessary until the intended result is achieved.
        

**What I Learned**

-   CyberChef provides a visual, recipe-based approach to data transformation and cryptography.
    
-   Operations are highly categorized and searchable, allowing efficient selection.
    
-   Input and output management features facilitate flexible workflow with files and multiple data sets.
    
-   A structured thought process helps systematically decode or transform data.
