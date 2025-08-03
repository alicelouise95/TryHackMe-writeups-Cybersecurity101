
### **TryHackMe: Cyber Security 101**

**Room:** `Hashing Basics`  
**Status:** Completed  
**Date:** 2025-08-03

----------

### **Goal**

Understand the fundamentals of hashing, its role in cybersecurity, how hash functions differ from encryption, password storage best practices, hash cracking techniques, and the use of hashing for data integrity and authentication.

---------

### **Key Topics Covered**


**1. Introduction to Hash Functions**

-   Hash functions produce a fixed-size output (hash or digest) from input data of any size.
    
-   They are one-way functions: irreversible, with no key involved, unlike encryption.
    
-   A good hash function is fast to compute but computationally infeasible to reverse.
    
-   Any slight change in input data causes a drastically different output (avalanche effect).
    
-   Examples include MD5, SHA-1, and SHA-256.
    
-   Illustrated by the difference between the binary values of letters ‘T’ and ‘U’ resulting in completely different hashes.
    

----------

**2. Importance and Use of Hashing in Cybersecurity**

-   Hashing helps verify data integrity and protect password confidentiality.
    
-   Passwords are stored as hashes; on login, the entered password is hashed and compared to stored hashes.
    
-   Hash collisions occur when different inputs produce the same hash, but good hash functions minimize this risk.
    
-   MD5 and SHA-1 are now considered insecure due to vulnerability to engineered collisions.
    

----------

**3. Insecure Password Storage Practices**

-   Plaintext password storage, deprecated encryption, and weak hashing algorithms are insecure.
    
-   Examples of real-world breaches:
    
    -   RockYou: stored plaintext passwords exposed.
        
    -   Adobe: used deprecated encryption and plaintext password hints.
        
    -   LinkedIn (2012): used insecure SHA-1 without salting.
        

----------

**4. Secure Password Storage Using Salting and Strong Hashes**

-   Salting involves adding a unique random value to each password before hashing to prevent rainbow table attacks.
    
-   Secure hashing algorithms include Argon2, Scrypt, Bcrypt, and PBKDF2.
    
-   Process:
    
    1.  Select a secure hashing function.
        
    2.  Add a unique salt to the password.
        
    3.  Concatenate password and salt.
        
    4.  Compute the hash of the combined string.
        
    5.  Store both the hash and the salt.
        

----------

**5. Recognizing and Understanding Password Hashes**

-   Various hash formats exist with identifying prefixes (e.g., `$y$` for yescrypt, `$2b$` for bcrypt).
    
-   Linux stores password hashes in `/etc/shadow`, Windows stores them in SAM.
    
-   Windows hashes (NTLM) resemble MD4/MD5 visually.
    
-   Tools like hashID aid in hash type recognition but can be unreliable without context.
    

----------

**6. Password Cracking Techniques**

-   Hashes cannot be decrypted; cracking involves hashing many guesses and comparing outputs.
    
-   Tools like Hashcat and John the Ripper utilize wordlists (e.g., rockyou.txt) to guess passwords.
    
-   Modern GPUs accelerate hash cracking due to parallel processing capabilities.
    
-   Some hashing algorithms (e.g., bcrypt) are designed to resist GPU speed-ups.
    
-   Running cracking tools natively on hosts yields better performance than in virtual machines.
    

----------

**7. Hashing for Integrity Checking**

-   Hashes verify file integrity by detecting any modification, even a single bit change.
    
-   Useful for confirming downloaded files match originals or identifying duplicate files.
    

----------

**8. HMAC (Keyed-Hash Message Authentication Code)**

-   HMAC combines a secret key with a hash function to verify both message authenticity and integrity.
    
-   Uses a process of padding, XOR operations, and double hashing with constants.
    
-   Expression:  
    `HMAC(K,M) = H((K⊕opad) || H((K⊕ipad) || M))`
    
-   Ensures that the sender is authenticated and the message is unaltered.
    

----------

**9. Differentiating Hashing, Encoding, and Encryption**

-   Hashing: One-way, fixed-size digest, irreversible.
    
-   Encoding: Transforming data into a compatible format (e.g., ASCII, UTF-8), reversible.
    
-   Encryption: Uses keys and ciphers to protect confidentiality, reversible with key access.
    

----------

### **What I Learned**

-   Hash functions provide irreversible, fixed-length data digests crucial for data integrity and authentication.
    
-   Hashing is distinct from encryption and encoding, each serving different security purposes.
    
-   Proper password storage requires strong hashing algorithms combined with unique salts to mitigate attacks.
    
-   Insecure password handling (plaintext, weak hashes, deprecated encryption) leads to severe breaches.
    
-   Hash cracking leverages computational power and large wordlists; GPU acceleration is common but countered by certain algorithms.
    
-   Hashing is essential for file integrity verification and detecting duplicates.
    
-   HMAC provides a robust method for verifying message authenticity and integrity using secret keys.
    
-   Recognizing various hash types and their storage locations aids in security analysis and penetration testing.
