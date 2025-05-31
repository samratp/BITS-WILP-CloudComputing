**Unit Testing for Security** involves writing automated tests that validate the security-related functionality of individual units of code (usually functions, methods, or classes) to ensure that security flaws are not introduced during development. While unit testing primarily focuses on correctness, it can also catch certain security vulnerabilities early in the software development lifecycle.

---

## **Why Unit Testing Matters for Security**

Security issues like **input validation errors**, **authentication flaws**, **access control bypasses**, or **insecure defaults** can often be prevented by thorough unit testing of security-sensitive logic.

---

## **Security Areas to Cover with Unit Tests**

Here are key areas to consider when writing unit tests for security:

### 1. **Input Validation**

Ensure all input is validated, sanitized, and normalized.

* Test for:

  * SQL injection
  * Cross-site scripting (XSS)
  * Path traversal
  * Command injection

**Example:**

```python
def test_input_sanitization():
    assert sanitize_input("<script>alert(1)</script>") == "&lt;script&gt;alert(1)&lt;/script&gt;"
```

---

### 2. **Authentication Logic**

Test password checks, login mechanisms, multi-factor authentication, etc.

**Example:**

```python
def test_password_hashing():
    hashed = hash_password("securepass")
    assert check_password("securepass", hashed)
```

---

### 3. **Authorization & Access Control**

Ensure users cannot access or modify data they're not allowed to.

**Example:**

```python
def test_user_cannot_access_others_data():
    response = get_user_data(requesting_user_id=2, target_user_id=1)
    assert response.status_code == 403
```

---

### 4. **Secure Defaults**

Test that configuration defaults are safe (e.g., permissions, encryption enabled).

**Example:**

```python
def test_encryption_enabled_by_default():
    config = get_default_config()
    assert config["encryption"] is True
```

---

### 5. **Error Handling & Information Leakage**

Test that error messages do not leak sensitive data.

**Example:**

```python
def test_error_message_does_not_reveal_stack_trace():
    response = app.simulate_error()
    assert "Traceback" not in response.text
```

---

### 6. **Rate Limiting and Throttling**

Ensure APIs or login endpoints have protection against brute-force attacks.

**Example:**

```python
def test_login_throttling():
    for _ in range(10):
        attempt_login("user", "wrongpassword")
    assert is_login_rate_limited("user")
```

---

## Tools & Frameworks

* **Python**: `unittest`, `pytest`, `nose2`
* **JavaScript**: `Jest`, `Mocha`, `Chai`
* **Java**: `JUnit`, `Mockito`
* **Security-specific tools**:

  * [Bandit (Python)](https://bandit.readthedocs.io/)
  * [ESLint security plugins (JavaScript)](https://github.com/nodesecurity/eslint-plugin-security)

---

## Best Practices

* **Automate security unit tests** and integrate them into CI/CD pipelines.
* Use **mocking and stubbing** to isolate security-critical units.
* Write **negative tests** (invalid input, unauthorized access).
* Combine with **integration and penetration testing** for layered security.
