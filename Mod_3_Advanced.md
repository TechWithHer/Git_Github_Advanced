## 📌 MODULE 3: Advanced Git Operations & Hands-on Practice

### 5.1 Advanced Git Operations
- `git stash`
- `git cherry-pick`
- `git rebase`
- Rebase vs merge

### 5.2 Logs & Maintenance
- Git logs and filtering
- Log slicing
- Concept of log rotation

### 5.3 Best Practices & Notes to Remember
- Commit message standards
- Branch naming conventions
- Security reminders
- Common mistakes to avoid

### 5.4 Hands-on Tasks
- Initialize and manage a Git repository
- Implement branching and merging
- Create and review Pull Requests
- Practice reset, revert, stash, and rebase
- Simulate a real-world team workflow


````md
# 📘 MODULE 4 – CI Pipelines & Automation (GitHub Actions)

---

## 🎯 Module Objective

This module explains **how automation protects production** by enforcing checks *before* code is merged.  
You will learn how **event-driven CI pipelines** act as the first line of defense in DevOps.

> 🔑 Core idea:  
> **Automation should stop bad code early, not clean up later.**

---

## 🧠 What to Study

---

## ⚡ Event-Driven Pipelines

### What Does Event-Driven Mean?

CI pipelines are triggered by **events**, not by humans.

Common GitHub events:
- `pull_request`
- `push`
- `workflow_dispatch`
- `schedule`

In professional DevOps:
- Pipelines react automatically
- Humans do not decide when checks run

> ✅ This removes human error and bias.

---

## 🔀 PR-Based CI

### What Is PR-Based CI?

CI pipelines that run **when a Pull Request is opened or updated**.

```text
Developer → Push Code → Open PR → CI Runs → Review → Merge
````

### Why PR-Based CI Is Critical

* Issues are caught **before merge**
* Reviewers see test results
* Broken code never reaches `main`

> ❌ CI after merge = already damaged production history

---

## ⚠️ Fail-Fast Philosophy

### What Is Fail-Fast?

If something is wrong:

* Fail immediately
* Fail loudly
* Fail early

### Why Fail-Fast Matters

* Saves time
* Saves compute cost
* Prevents cascading failures
* Protects production

> 🚨 The earlier a failure happens, the cheaper it is to fix.

---

## 🧪 Hands-On Lab – Build a CI Pipeline

---

## 🧩 Exercise – Create a CI Workflow

### Step 1: Create Workflow File

```text
.github/workflows/ci.yml
```

---

### Step 2: Add CI Configuration

```yaml
name: CI

on: [pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Run tests
        run: echo "Run tests here"
```

📌 This pipeline:

* Triggers on PR creation or updates
* Checks out the code
* Runs test commands (placeholder)

---

## 🧪 Testing the Pipeline

### Step 1: Open a Pull Request

* Push a feature branch
* Create PR targeting `main`

### Step 2: Observe CI Run

* Go to **PR → Checks tab**
* Watch pipeline execution
* Ensure job passes

---

## 🧠 Learning Outcome

* CI is automatic
* CI runs *before* merge
* PRs become quality gates

---

## 🤔 Reflection: Why CI Should Never Run After Merge

### 1️⃣ Damage Is Already Done

* Broken code is already in `main`
* History is polluted

### 2️⃣ Rollbacks Become Necessary

* Extra work
* Extra risk
* Lost time

### 3️⃣ Trust Is Reduced

* `main` should always be stable
* CI failure on `main` breaks confidence

> ✅ **Correct rule:**
> If CI fails → merge is blocked.

---

---

# 📘 MODULE 5 – Security, Secrets & Release Strategy

---

## 🎯 Module Objective

This module introduces **security-first thinking** and **controlled releases**, both essential for real-world DevOps systems.

> 🔐 DevOps is not just speed — it is **safe speed**.

---

## 🧠 What to Study

---

## 🔑 GitHub Secrets

### What Are GitHub Secrets?

Encrypted values used in workflows:

* API keys
* Tokens
* Passwords
* Cloud credentials

### Why Secrets Exist

* Prevent hardcoding sensitive data
* Centralized secret management
* Access-controlled and masked in logs

> ❌ Never store secrets in code or `.env` files in GitHub.

---

## 🔐 Protected Branches

Protected branches enforce:

* Mandatory PRs
* Required CI checks
* Required approvals
* Restricted force pushes

> 📌 Protection ensures **policy > privilege**.

---

## 🏷️ Semantic Versioning

### Version Format

```text
MAJOR.MINOR.PATCH
```

Example:

```text
v1.0.0
```

### Meaning:

* **MAJOR** → breaking changes
* **MINOR** → new features (backward compatible)
* **PATCH** → bug fixes

> Semantic versioning sets clear expectations for users.

---

## 🧪 Hands-On Lab

---

## 🧩 Exercise 1 – Release Tagging

### Step 1: Create a Tag

```bash
git tag v1.0.0
git push origin v1.0.0
```

📌 Tags mark **immutable release points**.

---

### Step 2: Create a GitHub Release

Include release notes:

#### 🚀 Features

* List new features introduced

#### 🐞 Fixes

* List resolved bugs

#### ⚠️ Known Issues

* Document limitations or bugs

> Release notes are a contract with users.

---

## 🧩 Exercise 2 – Security Thinking

---

## 📝 Short Note: What Would Break If a Secret Leaked?

If a secret leaks:

### 1️⃣ Infrastructure Compromise

* Cloud resources can be deleted
* Servers can be hijacked
* Data can be stolen

### 2️⃣ Financial Loss

* Unauthorized cloud usage
* Unexpected billing spikes

### 3️⃣ Production Outage

* Services can be shut down
* Deployments can fail

### 4️⃣ Trust & Compliance Damage

* Customer trust is lost
* Legal and compliance issues arise

### 5️⃣ Emergency Rotation Required

* Secrets must be revoked
* Pipelines may break temporarily

> 🔴 **Secrets leakage is a production incident, not a mistake.**

---

## ✅ Key Takeaways

* CI must run before merge
* Fail fast saves systems
* Secrets must never be in code
* Protected branches enforce discipline
* Releases must be versioned and documented

---

📌 *These modules reflect industry-grade DevOps practices used in secure, scalable engineering teams.*

➡️ **Next Module:**
Monitoring, Alerts & Incident Response in DevOps

```
```
