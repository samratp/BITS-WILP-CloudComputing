### Example: SAST Concepts (Source, Sink, Taint, Vulnerability, CFG, Path Traversal, Apply Checking)

**Language:** Python (for clarity)
**Topic:** Static Application Security Testing

---

#### Code Snippet (Vulnerable)

```python
import os
from flask import request

@app.route('/read_file')
def read_file():
    filename = request.args.get('file')  # Source
    with open("/var/data/" + filename, 'r') as f:  # Sink
        return f.read()
```

---

#### Step-by-Step SAST Analysis

**1. Source**

```python
filename = request.args.get('file')
```

* This is untrusted user input from a query parameter.
* **Marked as a tainted source**.

**2. Sink**

```python
open("/var/data/" + filename, 'r')
```

* Critical operation (file access) that uses untrusted input.
* **Sink for path traversal** vulnerabilities.

**3. Taint Propagation**

* `filename` is tainted from the source.
* It is used directly in the file path without sanitization.
* **Taint flows from source → sink**.

**4. Vulnerability Detected**

* No validation or sanitization is performed.
* Attacker can input:
  `file=../../../../etc/passwd`
* This results in a **Path Traversal** vulnerability.

**5. Control Flow Graph (CFG)**

* The flow is linear:

  1. Input received
  2. File opened with that input
  3. Content returned

* In more complex code, CFG helps analyze branches (e.g., `if`, `try/except`) to see if checks exist.

**6. Apply Checking**

* The SAST tool would apply semantic rules like:

  * "Untrusted input should not reach `open()` without sanitization"
  * No regex/path normalization/safety check is present
  * Therefore, the rule **fails**, and a vulnerability is reported

---

#### Secure Version (Fixed)

```python
import os
from flask import request, abort

@app.route('/read_file')
def read_file():
    filename = request.args.get('file')
    if not filename or '..' in filename or filename.startswith('/'):
        abort(400, "Invalid filename")  # Basic sanitization

    safe_path = os.path.join("/var/data", filename)
    with open(safe_path, 'r') as f:
        return f.read()
```

* Taint is neutralized through validation.
* CFG now includes a conditional check (`if`) which blocks malicious paths.
* Apply checking rules would now **pass**.

---

This illustrates how SAST tools trace data flows from **source → sink**, analyze **control flow**, and apply **security rules** to detect vulnerabilities like **path traversal**.
