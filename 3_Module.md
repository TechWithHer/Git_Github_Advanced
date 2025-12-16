
## 📌 MODULE 3: Authentication, Access & Security

### 3.1 Authentication Methods
- Password authentication (deprecated)
- Personal Access Tokens (PAT)
- SSH-based authentication

### 3.2 Personal Access Tokens (PAT)

1. What is a PAT?

A Personal Access Token (PAT) is a secure string of characters that acts like a password. It’s used to authenticate with GitHub (or other Git platforms) for API access, Git operations, and automation. Think of it as an alternative to your account password, especially after password-based authentication is deprecated.

2. Why PAT is Required

GitHub no longer allows password authentication for Git operations over HTTPS.

PAT is required for:
- Pushing/pulling code to repositories via HTTPS
- Accessing GitHub API programmatically
- Automating workflows (CI/CD pipelines)
- Provides more control and security than using your main account password.

3. Token Scopes and Permissions

- When creating a PAT, you choose scopes (what the token can do). Examples:
repo → Full control of private & public repositories
workflow → Access GitHub Actions workflows
admin:org → Manage organization settings
read:packages → Read-only access to packages

Tip: Always follow the principle of least privilege → only grant permissions required for your task.

4. Important Notes and Best Practices

- Keep it secret: Treat PAT like a password; don’t share it.
- Use different tokens for different purposes (automation, personal projects, CI/CD).
- Set expiration dates → limits risk if leaked.
- Revoke immediately if you suspect compromise.
- Avoid embedding PAT in code → use environment variables or secret managers.
- Use HTTPS with PAT instead of SSH if you prefer token-based authentication.

✅ Summary:
PAT is a secure, permission-based token used to authenticate and interact with GitHub instead of passwords. It improves security, supports automation, and is mandatory for HTTPS Git operations now.


### 3.3 SSH Keys

## **1. Public and Private Keys**

SSH uses **asymmetric cryptography**, which means two keys:

| Key Type        | Purpose                                 | Where it Lives        |
| --------------- | --------------------------------------- | --------------------- |
| **Private Key** | Secret key that **you keep safe**       | Your local machine    |
| **Public Key**  | Shared key that **remote server knows** | GitHub, servers, etc. |

✅ Key point: The **private key never leaves your machine**. Only the public key is shared.

---

## **2. How SSH Authentication Works**

1. **You generate a key pair**: `ssh-keygen` creates a public and private key.
2. **Add the public key to GitHub** (or any server).
3. **When you connect via SSH**:

   * GitHub sends a challenge encrypted with your **public key**.
   * Your **private key decrypts it** and proves your identity.
4. **Connection is established securely**; no password required.

📌 Example workflow with Git:

```text
git clone git@github.com:username/repo.git
# Uses SSH key authentication
```

---

## **3. Why SSH is Preferred in DevOps**

1. **Passwordless Automation**
   * CI/CD pipelines can push/pull code without human intervention
    
2. **Stronger Security**
   * Keys are much harder to brute-force than passwords.
     
3. **Works Behind Firewalls**
   * Unlike HTTPS, SSH can handle restricted network environments more reliably.
     
4. **Version Control Integration**
   * Most DevOps tools (Jenkins, GitLab runners, Terraform) natively support SSH for secure operations.
     
5. **Ease of Scaling**
   * Adding new machines only requires adding their public keys—no password sharing needed

---

### **Summary**

* **Private Key** = Your secret, stays with you.
* **Public Key** = Shared with servers.
* SSH authentication = Private key proves your identity to the server.
* **Why DevOps loves it** = Secure, automated, and scalable.

---

