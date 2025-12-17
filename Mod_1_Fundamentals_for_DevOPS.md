
# 📘 MODULE 1: SCM, VCS, Git & GitHub Fundamentals for DevOps

---

## 1️⃣ Source Code Management (SCM)

**Definition & Purpose:**
Source Code Management (SCM) is the discipline and tools used to **track changes, manage code, and enable collaboration** among developers. It is essential for maintaining code quality, version history, and supporting team collaboration in fast-paced DevOps environments.

**Role in DevOps & Agile:**

* **Agile** → Determines what to build and how often.
* **DevOps** → Determines how to build, test, and deliver it efficiently.
* **SCM** → Connects both, ensuring smooth collaboration, code tracking, and version control.

**Types of SCM:**

| Type                | Description                                                                        | Example                | Typical Users                                                                             |
| ------------------- | ---------------------------------------------------------------------------------- | ---------------------- | ----------------------------------------------------------------------------------------- |
| **Centralized SCM** | Single central repository. Network required for commit. Limited offline work.      | SVN                    | Legacy enterprises, banks, government departments, mainframe/monolithic application teams |
| **Distributed SCM** | Each developer has a full repository copy. Works offline, faster, safer, flexible. | Git, Mercurial, Bazaar | Modern DevOps teams, startups, cloud-based development                                    |

**In Short:**

* Centralized = One source
* Distributed = Many synchronized sources

**Key Clarification:**

* Git = tool (VCS)
* GitHub = platform (SCM)
* SCM = discipline/process
* VCS = version tracking system

---

## 2️⃣ Version Control System (VCS)

**Definition:**
A Version Control System (VCS) is software that **tracks changes in files**, maintains history, and allows rollback.

**File System vs VCS:**

* File system → Stores files, no history.
* VCS → Stores files **and their version history**, enabling collaboration.

**Types of VCS:**

1. **Local** → Single developer, versions stored locally
2. **Centralized** → Single server repository, multiple users
3. **Distributed** → Full repository copy on each developer’s machine (Git)

---

## 3️⃣ Git Basics

**What is Git:**

* **Git** is a distributed version control system created by Linus Torvalds in 2005.
* Tracks changes, supports branching/merging, offline commits, and collaboration.

**Why Git in DevOps:**

* Supports **fast, collaborative workflows**
* Enables **branching strategies** for CI/CD pipelines
* Integrates with automation (GitHub Actions, Jenkins, etc.)

**Git Architecture:**

| Component         | Description                                                  |
| ----------------- | ------------------------------------------------------------ |
| Working Directory | Your local files you’re actively editing                     |
| Staging Area      | Temporarily holds files ready to commit (`git add`)          |
| Local Repository  | Stores committed snapshots locally                           |
| Remote Repository | Centralized copy on GitHub/GitLab/Bitbucket for team sharing |

---

## 4️⃣ Git Platforms

| Platform       | Purpose                                          |
| -------------- | ------------------------------------------------ |
| GitHub         | Cloud-based Git repository, DevOps collaboration |
| GitLab         | Git repository + CI/CD pipelines                 |
| Bitbucket      | Git hosting, Jira integration                    |
| AWS CodeCommit | Managed Git service on AWS                       |
| Azure Repos    | Git hosting integrated with Azure DevOps         |

---

## 5️⃣ Git Workflow & Core Commands

### Git File States

| State     | Description                        |
| --------- | ---------------------------------- |
| Untracked | New file, not added to Git         |
| Tracked   | Already under Git version control  |
| Modified  | Tracked file changed locally       |
| Staged    | Ready to commit (`git add`)        |
| Committed | Saved snapshot in local repository |

**File Lifecycle Example:**
Untracked → Modified → Staged → Committed → Pushed to Remote

---

### Essential Git Commands

**Repository Setup:**

```bash
git init          # Initialize a repo
git clone <URL>   # Clone a remote repo
```

**Daily Workflow:**

```bash
git status        # Check file states
git add <file>    # Stage files
git commit -m ""  # Commit changes
git diff          # View differences
```

**History & Inspection:**

```bash
git log           # View commit history
git show <commit> # See commit details
git blame <file>  # Track last changes per line
```

---

### Git Ignore & Basic Hygiene

* `.gitignore` → Specify files/folders Git should ignore
* Avoid committing temporary files, secrets, or binaries
* Common mistakes: committing `node_modules`, `.env`, or compiled binaries

---

## 6️⃣ GitHub for DevOps

### Platform Capabilities

GitHub is not just code hosting; it is a **full DevOps platform**:

| Capability    | Description                                   |
| ------------- | --------------------------------------------- |
| Collaboration | Teams work together safely with PRs & reviews |
| Automation    | CI/CD, testing, security scans, deployment    |
| Governance    | Policies, audits, compliance, approvals       |

**Mindset Shift:**
GitHub = Control plane for software delivery, not just storage.

---

### Solo vs Team-Based GitHub Usage

| Aspect         | Solo                     | Team-Based DevOps                     |
| -------------- | ------------------------ | ------------------------------------- |
| Purpose        | Personal version control | Team collaboration & delivery         |
| Branching      | Often `main`             | Feature, release, hotfix              |
| Commits        | Direct commits           | Pull Requests (PRs)                   |
| Reviews        | Not required             | Mandatory code review                 |
| Quality Checks | Manual testing           | Automated CI checks                   |
| Issues         | Rare                     | Structured bug & task tracking        |
| Security       | Minimal                  | Protected branches, secrets, policies |
| Automation     | Optional                 | CI/CD with GitHub Actions             |

---

### Core GitHub Concepts

**Repositories** → Contain not just code, but **documentation, CI/CD workflows, security policies, IaC, templates, audit history**.

> Think of a repo as a **product**, not just files.

**Pull Requests (PRs)** → Quality gates for:

* Code review
* CI checks
* Security scans
* Compliance enforcement

**Issues** → Track:

* Features
* Bugs
* Tasks
* Technical debt
* Incidents

> Issues link to PRs for **traceability**.

**GitHub Actions** → Automation engine:

* Build/test pipelines
* Linting, code quality
* Security scans
* Deployment
* Notifications
  **Triggers:** push, PR, schedule, manual events

---

### Hands-On Exercise 1: DevOps-Ready Repository

**Objective:** Position a repo for **team-based DevOps workflow**

**Repository Description Checklist:**

1. What problem does the repo solve?
2. Who is it for?
3. How is it used in DevOps?

**Update `README.md` with:**

**Project Goal Example:**

```text
This project demonstrates a production-ready GitHub workflow
that enforces code quality, automates testing, and enables
continuous delivery using GitHub Actions.
```

**DevOps Workflow Diagram (ASCII):**

```text
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
```

---

## 7️⃣ Authentication, Access & Security

### Authentication Methods

* Password (deprecated)
* Personal Access Tokens (PAT)
* SSH-based authentication

---

### Personal Access Tokens (PAT)

**Definition:**
A secure token that acts like a password for GitHub API and Git operations.

**Why Required:**
GitHub **no longer supports password authentication** for HTTPS Git operations.

**Use Cases:**

* Push/pull over HTTPS
* API access
* CI/CD automation

**Token Scopes:**

* `repo` → Full repository control
* `workflow` → Access GitHub Actions
* `admin:org` → Organization settings
* `read:packages` → Read-only packages

**Best Practices:**

* Keep secret, don’t embed in code
* Use minimal permissions (least privilege)
* Expire and revoke if compromised
* Use environment variables or secret managers

**Summary:**
PAT = secure, scoped, automation-friendly alternative to passwords.

---

### SSH Keys

**1️⃣ Public & Private Keys**

| Key Type | Purpose                | Location             |
| -------- | ---------------------- | -------------------- |
| Private  | Secret, stays with you | Local machine        |
| Public   | Shared with server     | GitHub/remote server |

**2️⃣ SSH Authentication Workflow:**

1. Generate key pair: `ssh-keygen`
2. Add public key to GitHub
3. GitHub challenges encrypted with public key
4. Private key decrypts, proving identity
5. Connection established without passwords

**Example:**

```bash
git clone git@github.com:username/repo.git
```

**3️⃣ Why SSH in DevOps:**

* Passwordless automation for CI/CD
* Stronger security
* Works behind firewalls
* Native DevOps tool integration
* Easy scaling across machines

**Summary:**

* Private = stays with you
* Public = shared
* SSH = secure, automated, scalable authentication

---
