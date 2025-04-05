Here's a **detailed explanation of each security vulnerability**, including **what it is**, **why it's dangerous**, and a **practical example**.

---

## 🔐 **Authentication & Authorization Issues**

### 1. **Authentication Bypass**
**What:** Gaining access without proper credentials.  
**Example:** If a URL like `/admin` doesn’t check user roles, any user might access it directly.

---

### 2. **Missing/Incorrect Authorization**
**What:** Failing to check whether the authenticated user is allowed to perform an action.  
**Example:** A user can access another user's bank account by modifying the URL:  
`/accounts/view?userId=123 → /accounts/view?userId=124`

---

### 3. **Password Guessing**
**What:** Attacker tries many passwords until they find the correct one.  
**Example:** Brute force a login form with common passwords like "123456" or "admin123".

---

## ⚠️ **Input Validation Issues**

### 4. **Reliance on Untrusted Inputs**
**What:** Using external input (user, API, device) without validation.  
**Example:** Trusting form inputs to calculate prices may allow users to submit a cheaper price.

---

### 5. **Cross-Site Scripting (XSS)**
**What:** Injecting scripts into web pages viewed by others.  
**Example:**  
```html
<script>alert("Hacked!")</script>
```
Typed into a comment field, it runs when another user views the comment.

---

### 6. **Cross-Site Request Forgery (CSRF)**
**What:** Forcing users to perform actions without consent.  
**Example:** A malicious email contains:  
```html
<img src="http://bank.com/transfer?to=attacker&amount=1000">
```
If the user is logged in, this could transfer money automatically.

---

### 7. **SQL Injection**
**What:** Injecting SQL commands via user input.  
**Example:**  
Input: `' OR '1'='1`  
Query becomes:  
```sql
SELECT * FROM users WHERE username = '' OR '1'='1';
```
This bypasses login.

---

### 8. **OS Command Injection**
**What:** Executing arbitrary system commands.  
**Example:** A file upload script uses:  
```python
os.system("rm " + filename)
```
Inputting `"; rm -rf /` would wipe the server.

---

### 9. **Path Traversal**
**What:** Accessing files outside intended directories.  
**Example:**  
`/download?file=../../etc/passwd`  
Gives access to sensitive system files.

---

### 10. **XML External Entities (XXE)**
**What:** Abuse of XML parsers to access internal data.  
**Example:**
```xml
<!DOCTYPE foo [<!ENTITY xxe SYSTEM "file:///etc/passwd">]>
<note>&xxe;</note>
```
Returns the contents of `/etc/passwd`.

---

### 11. **Format String Injection**
**What:** Exploiting unfiltered input in functions like `printf`.  
**Example:**  
Input: `%x %x %x`  
Might leak memory addresses.

---

### 12. **Integer Overflow**
**What:** Numbers wrap around unexpectedly.  
**Example:**  
A system accepts a value up to 255. Inputting 256 wraps it to 0, allowing bypass.

---

### 13. **Buffer Overflow**
**What:** Writing past memory buffer boundaries.  
**Example:** A password field allows 10 characters but attacker sends 1000, overwriting memory and potentially executing code.

---

### 14. **Insecure Deserialization**
**What:** Executing code or changing logic via tampered serialized objects.  
**Example:**  
Send a serialized Java object with malicious commands, which gets executed when deserialized.

---

## 🔒 **Cryptographic Issues**

### 15. **Missing Encryption of Sensitive Data**
**What:** Storing or sending sensitive data in plaintext.  
**Example:** Passwords sent over HTTP instead of HTTPS can be sniffed.

---

### 16. **Use of a Broken Crypto Algorithm**
**What:** Using weak algorithms like MD5 or SHA1.  
**Example:** An attacker creates a hash collision and forges a signature.

---

### 17. **Unsalted Hash**
**What:** Hashing passwords without a unique salt.  
**Example:** Two users with password "1234" get the same hash, making it easier to crack.

---

### 18. **Download of Code Without Integrity Check**
**What:** Dynamically downloading and running code without verifying it.  
**Example:** A JS library downloaded during runtime is replaced by malicious code.

---

## 🌐 **Other Dangerous Practices**

### 19. **Open Redirect**
**What:** Redirecting users to untrusted sites using URL manipulation.  
**Example:**  
`/redirect?url=http://evil.com`  
Used for phishing attacks.

---

### 20. **Upload of Dangerous File**
**What:** Allowing upload of executable or script files.  
**Example:** An attacker uploads a `.php` shell script and accesses it remotely to control the server.

---
