
### **TryHackMe: Cyber Security 101**

**Room:** `Cryptography basics`  
**Status:** Completed  
**Date:** 2025-08-01

----------

### **Goal**

Understand the purpose and fundamental concepts of cryptography, including key terms, symmetric and asymmetric encryption, cryptographic algorithms, and essential mathematical operations used in encryption.

---------

### **Key Topics Covered**



**1. Purpose of Cryptography**

Cryptography enables secure communication in the presence of adversaries.  
Its core goals are:

-   **Confidentiality** – Prevent unauthorized access to data
    
-   **Integrity** – Ensure data hasn’t been altered
    
-   **Authenticity** – Verify the source of data
    

Cryptography is used extensively in everyday technologies, particularly encrypted internet communications.

----------

**2. Key Terminology**

-   **Plaintext** – The original readable data (e.g., documents, images, binary files)
    
-   **Ciphertext** – The unreadable, encrypted version of the plaintext
    
-   **Cipher** – The algorithm or method used for encryption and decryption
    
-   **Key** – A secret string of bits used by a cipher to perform encryption/decryption
    
-   **Encryption** – The process of converting plaintext into ciphertext using a cipher and key
    
-   **Decryption** – The reverse of encryption, converting ciphertext back to plaintext
    

_Note:_ The cipher itself is generally public, but the key must remain secret (except for public keys in asymmetric encryption).

----------

**3. Historical Cipher: Caesar Cipher**

One of the earliest known ciphers, where each letter in the plaintext is shifted by a fixed number to create ciphertext. It’s simple but easily broken by brute force.

----------

**4. Types of Encryption**

#### **Symmetric Encryption (Same Key)**

-   Uses the **same key** for both encryption and decryption
    
-   Requires a **secure channel** to share the key
    
-   Scalability becomes an issue with multiple recipients
    
-   Vulnerable if key is intercepted
    

**Examples:**

-   **DES** – 56-bit key, broken in <24 hours by 1999
    
-   **3DES** – Applies DES 3 times (168-bit key, 112-bit effective), deprecated in 2019
    
-   **AES** – Adopted in 2001; key sizes: 128, 192, or 256 bits
    

#### **Asymmetric Encryption (Key Pair)**

-   Uses a **key pair**: one public and one private
    
-   **Public key** encrypts, **private key** decrypts
    
-   No need to share private key — safer for open networks
    
-   Typically **slower** and requires **larger keys**
    

**Examples:**

-   **RSA** – Common key sizes: 2048, 3072, 4096 bits
    
-   **Diffie-Hellman** – Secure key exchange, uses 2048+ bit keys
    
-   **ECC** – More efficient, e.g., 256-bit ECC ≈ 3072-bit RSA security
    

Asymmetric encryption relies on **one-way mathematical problems**: easy to compute, extremely hard to reverse (e.g., would take millions of years with current tech).

----------

**5. Mathematical Building Blocks**

#### **XOR (Exclusive OR)**

A binary operation used in many cryptographic algorithms.  
Compares two bits:

-   Returns `1` if bits are different
    
-   Returns `0` if bits are the same
    

**Example:**  
`1001 ⊕ 1010 = 0011`

#### **Modulo Operation**

Returns the **remainder** when one number is divided by another.

**Examples:**

-   `25 % 5 = 0`
    
-   `23 % 6 = 5`
    
-   `23 % 7 = 2`
    

**Properties:**

-   Always returns a result between `0` and `n - 1` (where `n` is the divisor)
    
-   Used widely in hashing, key generation, and cryptographic primitives
    

----------

### **What I Learned**

-   Cryptography protects data confidentiality, integrity, and authenticity
    
-   Learned key terms: plaintext, ciphertext, cipher, key, encryption, decryption
    
-   Understood the Caesar Cipher as a historical encryption method
    
-   Explored symmetric encryption (DES, 3DES, AES) and its key management challenges
    
-   Grasped asymmetric encryption (RSA, ECC) and how public/private keys work
    
-   Saw how ECC achieves security with shorter keys compared to RSA
    
-   Learned how XOR and modulo operations are foundational in modern encryption
