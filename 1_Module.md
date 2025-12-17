# 📌 MODULE 1: SCM, VCS & Git Fundamentals

### 1.1 Source Code Management (SCM)
- What is SCM and why it is required: To track changes, manage code and create collaborative environment. 
- Role of SCM in DevOps and Agile: Agile tells what to build and how often. DevOps tells how to build, test, and deliver it fast. SCM connects both.
- Centralized vs Distributed SCM:

-- Centralized SCM: Single central repository, Requires network connection to commit, Limited offline work | Example: SVN

-- Distributed SCM: Every developer has a full repository copy, Commits work offline, Faster, safer, and more flexible | Example: Git, Murcurial, Bazaar

Common users of Centralized SCM: 
Legacy enterprises(banks, government departments, old IT service companies)
Mainframe / monolithic application teams
Highly controlled environments where strict access control is more important than speed

In short:
Centralized = one source
Distributed = many synchronized sources

Git = tool (VCS)
GitHub = platform (SCM)
SCM = discipline/process
VCS = version tracking system


### 1.2 Version Control System (VCS)
- What is a VCS
- File system vs Version Control System
- Types of VCS (Local, Centralized, Distributed)

### 1.3 Git Basics
- What is Git (full form and history)
- Why Git is used in DevOps
- Git architecture:
  - Working Directory
  - Staging Area
  - Local Repository
  - Remote Repository

### 1.4 Git Platforms
- GitHub
- GitLab
- Bitbucket
- AWS CodeCommit
- Azure Repos


## 📌 MODULE 2: Git Workflow & Core Commands

### 2.1 Git File States
- Tracked and Untracked files
- Modified, Staged, and Committed states
- File lifecycle in Git

### 2.2 Essential Git Commands
- Repository setup:
  - `git init`
  - `git clone`
- Daily workflow:
  - `git status`
  - `git add`
  - `git commit`
  - `git diff`
- History and inspection:
  - `git log`
  - `git show`
  - `git blame`

### 2.3 Git Ignore & Basic Hygiene
- Purpose of `.gitignore`
- Avoiding unnecessary files
- Common beginner mistakes

---

---
# 📘 What to Study: GitHub for DevOps (Collaboration • Automation • Governance)

---

## 🌍 GitHub as a Platform (Not Just Code Hosting)

GitHub is a **complete DevOps platform** that supports:

- **Collaboration** → Teams working together safely and efficiently  
- **Automation** → CI/CD, testing, security scans, deployments  
- **Governance** → Code ownership, approvals, compliance, audit trails  

> 🔑 **Mindset shift:**  
> GitHub is **not just a place to store code**.  
> It is a **control plane** for modern software delivery.

---

## 👤 Solo Developer Git Usage vs 👥 Team-Based DevOps GitHub Usage

| Aspect | Solo Developer | Team-Based DevOps |
|------|---------------|------------------|
| Purpose | Personal version control | Team collaboration & delivery |
| Branching | Often `main` only | Feature, release, hotfix branches |
| Commits | Direct commits to main | Commits via Pull Requests |
| Reviews | Not required | Mandatory code reviews |
| Quality Checks | Manual testing | Automated checks (CI) |
| Issues | Rare or informal | Structured task & bug tracking |
| Security | Minimal | Protected branches, secrets, policies |
| Automation | Optional | CI/CD pipelines using GitHub Actions |

---

## 🧠 Core GitHub Concepts You Must Understand

---

### 📦 Repository ≠ Code Only

A GitHub repository contains:

- Application source code
- Documentation (`README.md`, `docs/`)
- Infrastructure as Code (IaC)
- CI/CD workflows
- Security policies
- Issue & PR templates
- Audit history

> ✅ A repository represents a **product**, not just files.

---

### 🔀 Pull Requests (PRs) = Quality Gates

Pull Requests ensure:

- Code review before merge
- Automated testing is passed
- Security scans are executed
- Compliance rules are enforced

**PRs act as gates**, not suggestions.

---

### 🐞 Issues = Work Tracking System

GitHub Issues are used for:

- Feature requests
- Bugs
- Tasks
- Technical debt
- Incidents

Issues can be linked to PRs for **full traceability**.

---

### ⚙️ GitHub Actions = Automation Engine

GitHub Actions automate:

- Build & test pipelines
- Code quality checks
- Security scans
- Deployments
- Notifications

Triggered by:
- Push
- Pull Request
- Schedule
- Manual events

> GitHub Actions turn GitHub into a **CI/CD platform**.

---

## 🧪 Hands-On Exercise 1

### 🎯 Objective
Understand how to position a repository as a **DevOps-ready project**.

---

## 🧩 Exercise 1 – Repository Description

### 📝 Create a Repository Description That Answers:

**1. What problem does this repo solve?**  
> Example:  
> Automates testing and deployment to reduce manual errors and speed up releases.

**2. Who is it for?**  
> Example:  
> DevOps engineers, backend developers, and SRE teams.

**3. How is it used in DevOps?**  
> Example:  
> Used as a CI/CD pipeline source integrated with GitHub Actions.

---

## 📄 Update Your `README.md`

### Include the Following Sections:

---

## 🎯 Project Goal

Clearly explain:
- Why this project exists
- What DevOps problem it solves
- What outcome it delivers

Example:
```text
This project demonstrates a production-ready GitHub workflow
This project demonstrates a production-ready GitHub workflow
that enforces code quality, automates testing, and enables
continuous delivery using GitHub Actions.
```
## 🔄 DevOps Workflow Diagram (ASCII)

Developer
   |
   v
Feature Branch
   |
   v
Pull Request
   |
   +--> Code Review
   |
   +--> CI Pipeline
   |       - Lint
   |       - Test
   |       - Security Scan
   |
   v
Approved & Merged
   |
   v
Deployment Pipeline
   |
   v
Production


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



