### Source Code Signing and Image Signing

---

### **1. Source Code Signing**

#### **Definition:**

Source code signing is the process of **digitally signing source code files or commits** using **cryptographic keys** to prove authorship, integrity, and authenticity.

---

#### **Why It's Important:**

* Prevents tampering of source code.
* Confirms that code comes from a **trusted developer** or organization.
* Helps track accountability and ownership in collaborative environments.
* Required in **regulated environments** or for open-source trustworthiness.

---

#### **How It Works:**

* Developers use **public-key cryptography** (e.g., GPG/PGP) to sign code.
* The signature is embedded in the commit or tag.
* Others can verify the signature using the developer's **public key**.

---

#### **Example – Git Commit Signing with GPG:**

```bash
git commit -S -m "Add authentication module"
```

* `-S` flag signs the commit.
* GitHub shows a **“Verified” badge** if the signature is valid and trusted.

---

#### **Use Cases:**

* Open-source projects (e.g., Linux kernel, Kubernetes).
* Enterprises requiring traceable source contributions.
* CI/CD pipelines ensuring that only signed commits trigger builds.

---

### **2. Image Signing**

#### **Definition:**

Image signing is the process of **cryptographically signing container or VM images** to ensure they have not been altered and come from a **trusted source**.

---

#### **Purpose in Cloud Security:**

* Prevents deployment of tampered or malicious images.
* Enables verification of **image provenance** and integrity.
* Essential for **secure supply chain practices**.

---

#### **How It Works:**

1. An image (e.g., Docker image) is built and **signed** using a signing tool.
2. The signature is stored in a **public log** or attached to the image metadata.
3. During deployment, tools **verify the signature** before running the image.

---

#### **Popular Tools:**

| Tool                           | Description                                                                         |
| ------------------------------ | ----------------------------------------------------------------------------------- |
| **Cosign**                     | From Sigstore; signs and verifies container images. Integrates with Kubernetes.     |
| **Notary v2**                  | Successor to Docker Content Trust; enables secure distribution of signed images.    |
| **Docker Content Trust (DCT)** | Legacy tool for image signing using Notary.                                         |
| **Sigstore Bundle**            | Includes `cosign`, `fulcio` (certificate issuance), and `rekor` (transparency log). |

---

#### **Example – Signing with Cosign:**

```bash
cosign sign --key cosign.key myrepo/myimage:latest
```

* Signature is stored in the container registry.
* Can be verified with:

```bash
cosign verify --key cosign.pub myrepo/myimage:latest
```

---

#### **Integration in Secure Software Pipelines:**

* Enforce **image policy validation** using tools like **Kyverno**, **OPA Gatekeeper**, or **Sigstore Policy Controller**.
* Block unsigned or untrusted images at **Kubernetes admission control**.

---

### **Comparison:**

| Aspect            | Source Code Signing           | Image Signing                        |
| ----------------- | ----------------------------- | ------------------------------------ |
| Purpose           | Ensure trust in code authors  | Ensure trust in deployment artifacts |
| Tooling           | GPG, SSH, GitHub, GitLab      | Cosign, Notary, Docker DCT           |
| Integration Point | Code repositories             | Container registries, CI/CD          |
| Outcome           | Verified authorship/integrity | Verified image provenance/integrity  |

---

### **Conclusion:**

In Secure Software Engineering, **source code and image signing** are critical for maintaining the **integrity and provenance** of software artifacts throughout the development and deployment lifecycle. They are foundational to **supply chain security**, enabling trust in both code and the environments it runs in.
