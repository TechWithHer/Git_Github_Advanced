

# 📘 MODULE 4: Branching, Collaboration & History Management

---

## 🎯 Module Objective

This module explains **how professional DevOps teams control change and reduce production risk** using:

* Branching strategies
* Pull Request (PR)–driven development
* Quality gates, reviews, and Git hygiene

> By the end of this module, you’ll understand **why stable production systems depend more on process than individual skill**.

---

## 1️⃣ Branching in Git

**What is Branching?**
Branching allows you to **create independent lines of development**. Each branch can contain new features, bug fixes, or experiments without affecting production code.

**Why Branching Matters in Teams:**

* Enables multiple developers to work simultaneously
* Reduces risk of breaking `main`
* Facilitates PR-based reviews and approvals

**Core Branch Commands:**

```bash
git branch           # List, create, or delete branches
git checkout <branch>  # Switch to a branch
git switch <branch>    # Modern way to switch branches
git merge <branch>     # Merge changes into current branch
```

---

## 2️⃣ Branching Strategies (Industry Use)

| Strategy                  | Description                                                                           |
| ------------------------- | ------------------------------------------------------------------------------------- |
| Feature Branching         | Each feature in its own branch, merged via PR                                         |
| Git Flow                  | Standardized workflow with `main`, `develop`, `feature`, `release`, `hotfix` branches |
| Trunk-Based Development   | Short-lived branches, frequent merges to `main`                                       |
| Release & Hotfix Branches | Controlled production releases and urgent fixes                                       |

---

## 3️⃣ Collaboration on GitHub

**Pull Requests (PRs):** Central mechanism for team collaboration

* Add reviewers & collaborators
* Discuss and review code
* Enforce CI checks and security scans
* Record decisions and maintain audit trails

> ✅ **PRs = Quality Gates**

---

## 4️⃣ History Management & Undoing Changes

| Command               | Purpose                                                                               |                   |                                 |
| --------------------- | ------------------------------------------------------------------------------------- | ----------------- | ------------------------------- |
| `git revert <commit>` | Creates a new commit that undoes changes                                              |                   |                                 |
| `git reset [--soft    | --mixed                                                                               | --hard] <commit>` | Moves HEAD to a previous commit |
| Revert vs Reset       | Revert is safe for shared branches; Reset rewrites history, risky for shared branches |                   |                                 |

---

## 🔐 Protecting `main` Branch

**Why Protect `main`:**

* Prevent untested code from entering production
* Ensure mandatory reviews
* Maintain audit trails

**Protection Features:**

* Mandatory Pull Requests
* Required reviews
* Automated CI/CD checks
* Clear ownership and traceability

> ❌ **Golden Rule:** No direct pushes to `main`, even by senior engineers

---

## 🌱 Feature vs 🔥 Hotfix Branches

### Feature Branches (`feature/*`)

Purpose: New features, enhancements, documentation, refactoring

```bash
feature/add-readme-section
feature/user-authentication
feature/api-logging
```

Characteristics:

* Created from `main`
* Short-lived
* Merged only via PR
* Low production risk

### Hotfix Branches (`hotfix/*`)

Purpose: Urgent production bugs, critical failures, security vulnerabilities

```bash
hotfix/payment-crash
hotfix/auth-token-expiry
```

Characteristics:

* High priority
* Minimal and focused changes
* Require PR approval

> 🚨 Urgency does NOT bypass PR process

---

## 🔁 PR-Driven Development

**Steps:**

1. Start in a branch
2. Open a Pull Request
3. Review & discuss changes
4. Pass automated checks
5. Merge into `main`

**PR Benefits:**

* Quality gates
* Risk filters
* Collaboration & knowledge sharing
* Audit and traceability

> ❌ No PR → No merge → No production impact

---

## 🧭 Recommended Branching Strategy

```text
main        → production-ready code
feature/*   → new development work
hotfix/*    → urgent production fixes
```

**Visual Flow:**

```text
main
 ├── feature/add-readme-section
 ├── feature/new-api
 └── hotfix/critical-bug
```

---

## 🧪 Hands-On Lab

### Exercise 1 – Branch Protection

**Step 1: Create a Feature Branch**

```bash
git checkout -b feature/add-readme-section
```

**Step 2: Make a Small Change**

* Add section to `README.md`
* Fix typo
* Improve documentation

**Step 3: Commit Changes**

```bash
git add README.md
git commit -m "Add usage section to README"
```

**Step 4: Push Branch**

```bash
git push origin feature/add-readme-section
```

**Step 5: Open a Pull Request**

* Base: `main`
* Compare: `feature/add-readme-section`
* Add title & description

**Conceptual Learning:**

* Avoided direct push to `main`
* Enabled review, discussion, and safe merging

---

### Exercise 2 – Pull Request Quality

**Create a PR Template:**
`.github/PULL_REQUEST_TEMPLATE.md`

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

**Benefits:**

* Consistent PR quality
* Clear testing steps
* Fewer production bugs

> 📌 PR templates **force engineers to think before merging**

---

## 🔀 Merge vs Rebase

### Merge

* Combines branches, creates **merge commit**

```bash
git merge feature/add-readme-section
```

**Pros:** Preserves history, safe for shared branches
**Cons:** History can be noisy

### Rebase

* Replays commits on top of another branch for **linear history**

```bash
git rebase main
```

**Pros:** Clean, readable history
**Cons:** Rewrites history, risky for shared branches

> 🚨 Never rebase shared branches

---

## 🧹 Squash Commits

* Combine multiple small commits into **one meaningful commit**
* GitHub PRs allow **Squash & Merge**
* Improves readability and maintainability

---

## ✍️ Reset (Safe Practice)

| Type       | Command                   | Effect                                  |
| ---------- | ------------------------- | --------------------------------------- |
| Soft Reset | `git reset --soft HEAD~1` | Undo commit, keep changes staged        |
| Hard Reset | `git reset --hard HEAD~1` | Undo commit, discard changes completely |

> ⚠️ Hard reset deletes work permanently

---

## 🚫 When NOT to Rewrite History

* Branch already pushed
* Branch shared with teammates
* Code merged into `main`
* Commit part of production release
* CI/CD pipelines depend on commit SHA

> Broken history = higher risk than messy history

---

## ✅ Key Takeaways

* `main` = sacred → protect it
* Branches = risk isolation
* PRs = enforce discipline
* Templates = improve quality automatically
* Merge = safe; Rebase = clean but risky; Squash = clarity
* **Process > hero coding**

---

📌 *This module reflects real-world GitHub and enterprise DevOps practices.*

➡️ **Next Module:** Tagging, Releases & Semantic Versioning

---

I can also **merge Modules 1–4 into a single master study guide** with hands-on commands, diagrams, and practical exercises, so you get **one complete reference for Git & GitHub in DevOps**.

Do you want me to do that next?
