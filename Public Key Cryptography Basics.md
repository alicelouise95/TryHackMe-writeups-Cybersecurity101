
### **TryHackMe: Cyber Security 101**

**Room:** `Public Key Cryptography Basics`  
**Status:** Completed  
**Date:** 2025-08-02

----------

### **Goal**

To understand the fundamental concepts of public key (asymmetric) cryptography, including its role in secure communication, key exchange methods, encryption algorithms, and practical applications like SSH, digital signatures, certificates, and PGP/GPG.

---------

### **Key Topics Covered**

**1. Fundamentals of Public Key Cryptography and Symmetric Encryption**

-   Public key cryptography uses a pair of keys: a **public key** (distributed openly) and a **private key** (kept secret).
    
-   It ensures **authentication**, **authenticity**, **integrity**, and **confidentiality** in communication.
    
-   Asymmetric cryptography is slower than symmetric encryption, so it is primarily used to securely exchange symmetric keys.
    
-   After key exchange, symmetric encryption (which uses a single shared secret key) is used for efficient data encryption and decryption.
    
-   Digital signatures and certificates help verify identities, preventing man-in-the-middle attacks.
    

----------

**2. RSA Encryption Algorithm**

-   RSA is a widely used asymmetric encryption algorithm based on the difficulty of factoring large numbers.
    
-   It involves selecting two large prime numbers (p and q), calculating n = p × q, and deriving public (n, e) and private (n, d) keys.
    
-   Encryption and decryption are done using modular exponentiation:
    
    -   Encryption: y=xemod  ny = x^e \mod ny=xemodn
        
    -   Decryption: x=ydmod  nx = y^d \mod nx=ydmodn
        
-   The security of RSA relies on the computational infeasibility of factoring very large numbers (hundreds of digits).
    

----------

**3. Diffie-Hellman Key Exchange**

-   A method for two parties to securely agree on a shared secret key over an insecure channel without prior shared secrets.
    
-   Both parties agree publicly on a large prime ppp and a generator ggg.
    
-   Each party chooses a private key, computes a public key using modular exponentiation, exchanges the public keys, then calculates the shared secret key.
    
-   The shared secret is gabmod  pg^{ab} \mod pgabmodp, computed independently by both parties.
    
-   Diffie-Hellman is often combined with RSA, where Diffie-Hellman handles key agreement and RSA manages digital signatures and authentication.
    

----------

**4. Secure Shell (SSH) and Key-based Authentication**

-   SSH uses public key cryptography to establish secure remote connections.
    
-   The client verifies the server's public key fingerprint to prevent man-in-the-middle attacks.
    
-   SSH supports password and key-based authentication; key-based is more secure.
    
-   Keys are generated with `ssh-keygen`, creating a public-private key pair.
    
-   The public key is stored in the server’s `~/.ssh/authorized_keys` file; private keys must be kept secret with strict file permissions.
    
-   SSH keys can stabilize reverse shells and can be used as persistent backdoors if left improperly managed.
    
-   Commands like `ssh-copy-id` simplify copying the public key securely to servers.
    

----------

**5. Digital Signatures and Certificates**

-   Digital signatures prove the authenticity and integrity of digital messages or documents.
    
-   Created by encrypting a hash or the message with a private key; verified using the corresponding public key.
    
-   Certificates provide trust by linking a public key to an identity via a chain of trust anchored by trusted Certificate Authorities (CAs).
    
-   HTTPS relies on certificates to ensure the client is communicating with a legitimate server.
    
-   The chain of trust ensures browsers trust certificates signed by recognized CAs.
    

----------

**6. PGP and GPG Encryption**

-   PGP (Pretty Good Privacy) and its open-source variant GPG implement encryption and digital signing.
    
-   Commonly used to secure emails by encrypting content and verifying sender identity.
    
-   Private keys can be protected with passphrases, which can be cracked using tools like John the Ripper in CTF contexts.
    
-   Understanding how to use GPG is essential for decrypting encrypted files or verifying signatures in security challenges.
    

----------

### **What I Learned**

-   The critical role of asymmetric cryptography in securely exchanging symmetric keys for efficient encryption.
    
-   How RSA works mathematically and why factoring large numbers is difficult.
    
-   The steps and principles behind the Diffie-Hellman key exchange for establishing shared secrets.
    
-   The process of SSH key-based authentication and its importance for secure remote connections.
    
-   How digital signatures and certificates enable authentication and trust in digital communication.
    
-   The practical uses of PGP/GPG in securing emails and files, including the importance of protecting private keys.
    
-   The interconnectedness of cryptographic methods to provide comprehensive security in real-world protocols.
