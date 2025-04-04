### 🕵️‍♂️ **Cryptanalysis: Breaking the Code**

Cryptanalysis is the **study and practice of breaking cryptographic systems**—finding weaknesses or flaws to reveal the plaintext or key **without having direct access** to the secret key.

---

## 🔍 **Types of Cryptanalysis Attacks**

---

### 1. **Frequency Analysis**
- One of the oldest forms of cryptanalysis.
- **Used on substitution ciphers** (like Caesar Cipher or monoalphabetic ciphers).
- Assumes that **letters appear with predictable frequency** in a given language.

#### 📌 Example:
In English:
- E, T, A, O are the most common letters.
- If a cipher letter appears often, it may stand for one of these.

#### 🔓 **Used to break:**
- Simple substitution ciphers
- Classical ciphers (e.g., Caesar Cipher, Vigenère Cipher)

---

### 2. **Known-Plaintext Attack (KPA)**
- The attacker has **some samples of plaintext** and their matching ciphertext.
- Goal: Use this to figure out the **key** or decrypt other ciphertexts.

#### 📌 Example:
If you know the phrase "Hello" is encrypted to "Wkrru", you can infer the shift in a Caesar Cipher.

#### 🔓 **Risk for:**
- Weak implementations of symmetric encryption
- Encrypted file headers or protocols with known patterns

---

### 3. **Chosen-Ciphertext Attack (CCA)**
- The attacker can **choose ciphertexts** and get them decrypted by the system.
- Uses the decrypted results to find the **encryption key** or forge valid messages.

#### 📌 Example:
- Used in the **Bleichenbacher attack** on RSA (against improperly padded messages).
- Attacker sends modified ciphertexts and watches system responses.

#### 🔓 **Countermeasures:**
- Use padding schemes like **OAEP**
- Use authenticated encryption (e.g., AES-GCM)

---

### 4. **Side-Channel Attack**
- Exploits **physical properties** of the cryptosystem:
  - Power consumption  
  - Timing  
  - Electromagnetic leaks  
  - Acoustic noise

#### 📌 Example:
- Measuring how long a device takes to perform decryption can leak information about the key.

#### 🔓 **Used to attack:**
- Smart cards  
- Hardware wallets  
- Embedded systems (IoT)

#### 🛡️ **Protection:**
- Constant-time algorithms  
- Physical shielding  
- Random delays  

---

### 📚 Summary Table:

| Attack Type              | What It Uses                         | Target             | Defense                              |
|--------------------------|--------------------------------------|--------------------|---------------------------------------|
| **Frequency Analysis**   | Letter frequencies                   | Simple ciphers     | Use strong, randomized encryption     |
| **Known-Plaintext**      | Plaintext + ciphertext pairs         | Symmetric systems  | Key rotation, salting, strong keys    |
| **Chosen-Ciphertext**    | Decryption oracle                    | RSA, block ciphers | Padding schemes, authenticated modes |
| **Side-Channel**         | Physical info (power, timing, etc.)  | Hardware devices   | Constant-time code, shielding         |

---
