## 📌 MODULE 4: Branching, Collaboration & History Management

### 4.1 Branching in Git
- What is branching
- Why branching matters in teams
- Branch commands:
  - `git branch`
  - `git checkout`
  - `git switch`
  - `git merge`

### 4.2 Branching Strategies (Industry Use)
- Feature branching
- Git Flow
- Trunk-based development
- Release and hotfix branches

### 4.3 Collaboration on GitHub
- Pull Requests (PR)
- Adding reviewers and collaborators
- Code review workflow

### 4.4 History Management & Undoing Changes
- `git revert`
- `git reset`
  - Soft
  - Mixed
  - Hard
- Revert vs Reset

---

## 🎯 Module Objective

This module explains **how professional DevOps teams control change and reduce production risk** using:

- Branching strategies
- Pull Request (PR)–driven development
- Quality gates and reviews

By the end of this module, you’ll understand **why stable production systems depend more on process than on individual skill**.

---

## 🧠 What to Study

---

## 🔐 Why `main` Must Be Protected

The `main` branch represents **production-ready code**.

If `main` is not protected:
- Anyone can push broken or untested code
- Bugs can reach production instantly
- No review, no accountability
- No audit trail

### 🔒 What Protection Achieves

- Mandatory Pull Requests
- Required reviews
- Automated checks before merge
- Clear ownership and traceability

> ✅ **Golden Rule:**  
> No one should push directly to `main` — not even senior engineers.

---

## 🌱 Feature Branches vs 🔥 Hotfix Branches

---

### 🌱 Feature Branches (`feature/*`)

Used for:
- New features
- Enhancements
- Refactoring
- Documentation updates

Examples:
```bash
feature/add-readme-section
feature/user-authentication
feature/api-logging
````

**Characteristics:**

* Created from `main`
* Short-lived
* Merged only via Pull Request
* Low production risk

---

### 🔥 Hotfix Branches (`hotfix/*`)

Used for:

* Urgent production bugs
* Critical failures
* Security vulnerabilities

Examples:

```bash
hotfix/payment-crash
hotfix/auth-token-expiry
```

**Characteristics:**

* High priority
* Minimal and focused changes
* Still require PR approval

> 🚨 **Urgency does NOT mean bypassing process.**
> Hotfixes still go through PRs to avoid compounding failures.

---

## 🔁 PR-Driven Development

### What Is PR-Driven Development?

Every change must:

1. Start in a branch
2. Go through a Pull Request
3. Be reviewed and discussed
4. Pass checks
5. Be merged into `main`

### Why This Is Critical in DevOps

Pull Requests act as:

* Quality gates
* Risk filters
* Collaboration tools
* Documentation of decisions
* Audit records

> ❌ No PR → No merge → No production impact

---

## 🧭 Recommended Branching Strategy

```text
main        → production-ready code
feature/*   → new development work
hotfix/*    → urgent production fixes
```

### Visual Flow

```text
main
 ├── feature/add-readme-section
 ├── feature/new-api
 └── hotfix/critical-bug
```

---

## 🧪 Hands-On Lab

---

## 🧩 Exercise 1 – Branch Protection (Conceptual + Practical)

### Step 1: Create a Feature Branch

```bash
git checkout -b feature/add-readme-section
```

📌 Purpose:
Isolate your change from production.

---

### Step 2: Make a Small Change

Example:

* Add a new section to `README.md`
* Improve documentation
* Fix a typo

> Keep changes small and focused to reduce risk.

---

### Step 3: Commit the Change

```bash
git add README.md
git commit -m "Add usage section to README"
```

---

### Step 4: Push the Branch

```bash
git push origin feature/add-readme-section
```

---

### Step 5: Open a Pull Request

On GitHub:

* **Base branch:** `main`
* **Compare branch:** `feature/add-readme-section`
* Add a clear title and description

---

### 🧠 Conceptual Learning

**What you avoided:**

* Direct push to `main`

**What you enabled:**

* Review
* Discussion
* Safe merging
* Controlled production change

---

## 🧩 Exercise 2 – Pull Request Quality

---

## 📄 Create a PR Template

Create this file:

```text
.github/PULL_REQUEST_TEMPLATE.md
```

---

### ✅ Standard PR Template

```md
## 📌 What Changed
- Summary of changes
- Files or modules affected

## 🎯 Why It Changed
- Business or technical reason
- Problem being solved

## 🧪 How to Test
- Steps to verify the change
- Commands to run
- Expected outcome
```

---

## 🔍 Why PR Templates Matter

Without templates:

* Poor explanations
* Missed testing steps
* Risky merges

With templates:

* Consistent PR quality
* Faster reviews
* Fewer production bugs

> 📌 PR templates **force engineers to think before merging**.

---

## 🤔 Reflection: How Does This Reduce Production Risk?

### 1️⃣ Controlled Access to Production

* No direct pushes to `main`
* Only reviewed code is merged

### 2️⃣ Smaller, Safer Changes

* Feature branches isolate scope
* Easier rollback if needed

### 3️⃣ Shared Accountability

* Reviewers are recorded
* Decisions are documented
* Full audit trail exists

### 4️⃣ Better Testing Discipline

* Explicit testing steps
* Reviewers know exactly how to validate changes

---

## ✅ Key Takeaways

* `main` is sacred — protect it
* Branches isolate risk
* PRs enforce discipline
* Templates improve quality automatically
* **Process > hero coding**

---

📌 *This module reflects real-world GitHub practices used by professional DevOps teams.*

➡️ **Next Module:**
Automated CI checks on Pull Requests using GitHub Actions

```
```
