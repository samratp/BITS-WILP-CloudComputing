### 🔐 **Types of Cryptography**

Cryptography is used to **protect data and ensure secure communication**. Here are the main types:

---

## **1. Symmetric Cryptography (Secret-Key Encryption)**

- **Same key** is used for both encryption and decryption.  
- **Fast** and suitable for large volumes of data.  
- Key must be **shared securely**, which is a challenge.

### 🔑 Examples:
- **AES (Advanced Encryption Standard)**
- DES (outdated)
- ChaCha20

### ✅ Use Cases:
- File encryption
- Securing stored data (at rest)
- VPNs

---

## **2. Asymmetric Cryptography (Public-Key Encryption)**

- Uses a **pair of keys**:  
  - 🔓 **Public key** to encrypt  
  - 🔐 **Private key** to decrypt
- **More secure** for key exchange, but **slower** than symmetric.

### 🔑 Examples:
- RSA  
- ECC (Elliptic Curve Cryptography)  
- Diffie-Hellman (for key exchange)

### ✅ Use Cases:
- Digital signatures  
- TLS/SSL (HTTPS)  
- Email encryption (e.g., PGP)

---

## **3. Homomorphic Encryption**

- A form of encryption that allows **computations to be performed on encrypted data**, and the result—when decrypted—is the same as if operations were done on plain data.
- Enables **privacy-preserving data processing**.

### 🔑 Types:
- **Partially Homomorphic** (supports only one operation like addition or multiplication)  
- **Fully Homomorphic** (supports both addition and multiplication)

### ✅ Use Cases:
- Secure cloud computing  
- Privacy-preserving machine learning  
- Encrypted search  

---

### 📊 Summary Table:

| Type                  | Key Type             | Speed       | Security Level | Use Case                                      |
|-----------------------|----------------------|-------------|----------------|-----------------------------------------------|
| **Symmetric**         | Same key             | Very fast   | Moderate       | Encrypting large files, disk encryption       |
| **Asymmetric**        | Public/Private keys  | Slower      | High           | Secure key exchange, digital signatures       |
| **Homomorphic**       | Public/Private keys  | Very slow   | High           | Computing on encrypted data, privacy at scale |

---
