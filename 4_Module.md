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

````md
# 📘 MODULE 3 – Git Hygiene & History Control

---

## 🎯 Module Objective

This module focuses on **keeping Git history clean, meaningful, and safe**.  
Good Git hygiene makes repositories easier to:
- Review
- Debug
- Audit
- Maintain at scale

> 🔑 **Rule of thumb:**  
> Git history is a communication tool, not just a backup.

---

## 🧠 What to Study

---

## 🔀 Merge vs Rebase

Understanding the difference is critical for team-based DevOps workflows.

---

### 🔁 Merge

**What it does:**  
Combines branches by creating a **merge commit**.

```text
A---B---C main
     \
      D---E feature
           \
            M  (merge commit)
````

**Command:**

```bash
git merge feature/add-readme-section
```

**Pros:**

* Preserves full history
* Safe for shared branches
* Shows exactly when branches diverged

**Cons:**

* History can become noisy
* Extra merge commits

**Best used when:**

* Working on shared branches
* Merging feature → main via Pull Request
* Auditability is important

---

### 🔂 Rebase

**What it does:**
Replays commits on top of another branch, creating a **linear history**.

```text
Before:
A---B---C main
     \
      D---E feature

After Rebase:
A---B---C---D'---E'
```

**Command:**

```bash
git rebase main
```

**Pros:**

* Clean, linear history
* Easier to read commit logs

**Cons:**

* Rewrites commit history
* Dangerous on shared branches

**Best used when:**

* Cleaning up local feature branches
* Preparing a PR
* Working solo on a branch

> 🚨 **Never rebase shared branches.**

---

## 🧹 Squash Commits

### What Is Squashing?

Combining multiple small commits into **one meaningful commit**.

Example:

```text
Before:
fix typo
fix typo again
update readme
final fix

After Squash:
Add README usage section
```

### Why Squash?

* Removes noise
* Improves readability
* One commit = one logical change

### How Squash Is Done (PR Level)

GitHub allows:

* **Squash and merge**
* Keeps `main` history clean

> ✅ Recommended for most feature branches.

---

## ✍️ Rewriting History Responsibly

Rewriting history includes:

* Rebase
* Reset
* Amend commits

### Allowed When:

* Working on local branches
* Feature branch not yet shared
* Fixing mistakes before PR

### Dangerous When:

* Branch is already pushed and used by others
* Code exists in production

> 🔴 **Golden Rule:**
> Never rewrite history that others depend on.

---

## 🧪 Hands-On Lab

---

## 🧩 Exercise 1 – Rebase Flow

### Step 1: Switch to Feature Branch

```bash
git checkout feature/add-readme-section
```

---

### Step 2: Rebase on `main`

```bash
git rebase main
```

📌 Purpose:
Bring your feature branch up to date with the latest production code.

---

### Step 3: Resolve Conflicts (If Any)

If Git reports conflicts:

```bash
git status
```

* Open conflicted files
* Fix conflicts manually
* Mark as resolved:

```bash
git add <file>
git rebase --continue
```

---

### 🧠 Learning Outcome

* Conflicts are resolved **once**
* History stays linear
* Cleaner PR diff

---

## 🧩 Exercise 2 – Reset (Safe Practice)

---

### 🔹 Soft Reset

```bash
git reset --soft HEAD~1
```

**What it does:**

* Removes last commit
* Keeps changes staged

**Use when:**

* Commit message is wrong
* Want to combine commits

---

### 🔹 Hard Reset

```bash
git reset --hard HEAD~1
```

**What it does:**

* Deletes last commit
* Deletes changes completely

**Use when:**

* Experiment went wrong
* You want to discard changes entirely

> ⚠️ **Hard reset permanently deletes work.**

---

## 📌 Comparison Summary

| Command  | Affects History | Keeps Changes | Risk Level |
| -------- | --------------- | ------------- | ---------- |
| `--soft` | Yes             | Yes (staged)  | Low        |
| `--hard` | Yes             | No            | High       |

---

## 📄 Documentation Section

---

## 🚫 When NOT to Rewrite History

### Do NOT Rewrite History When:

1. Branch is already pushed to remote
2. Branch is shared with teammates
3. Code has been merged into `main`
4. Commit is part of production release
5. CI/CD pipelines rely on commit SHA

### Why?

* Breaks teammate branches
* Causes merge conflicts
* Invalidates audit logs
* Damages trust in repo history

> ❗ **In teams, broken history is worse than messy history.**

---

## ✅ Key Takeaways

* Merge = safe, verbose history
* Rebase = clean, dangerous if misused
* Squash = clarity and professionalism
* Reset is powerful — use carefully
* History is a contract with your team

---

📌 *This module reflects enterprise Git standards followed by mature DevOps teams.*

➡️ **Next Module:**
Tagging, Releases & Semantic Versioning

```
```



➡️ **Next Module:**
Automated CI checks on Pull Requests using GitHub Actions

```
```
````md
# 📘 MODULE 3 – Git Hygiene & History Control

---

## 🎯 Module Objective

This module focuses on **keeping Git history clean, meaningful, and safe**.  
Good Git hygiene makes repositories easier to:
- Review
- Debug
- Audit
- Maintain at scale

> 🔑 **Rule of thumb:**  
> Git history is a communication tool, not just a backup.

---

## 🧠 What to Study

---

## 🔀 Merge vs Rebase

Understanding the difference is critical for team-based DevOps workflows.

---

### 🔁 Merge

**What it does:**  
Combines branches by creating a **merge commit**.

```text
A---B---C main
     \
      D---E feature
           \
            M  (merge commit)
````

**Command:**

```bash
git merge feature/add-readme-section
```

**Pros:**

* Preserves full history
* Safe for shared branches
* Shows exactly when branches diverged

**Cons:**

* History can become noisy
* Extra merge commits

**Best used when:**

* Working on shared branches
* Merging feature → main via Pull Request
* Auditability is important

---

### 🔂 Rebase

**What it does:**
Replays commits on top of another branch, creating a **linear history**.

```text
Before:
A---B---C main
     \
      D---E feature

After Rebase:
A---B---C---D'---E'
```

**Command:**

```bash
git rebase main
```

**Pros:**

* Clean, linear history
* Easier to read commit logs

**Cons:**

* Rewrites commit history
* Dangerous on shared branches

**Best used when:**

* Cleaning up local feature branches
* Preparing a PR
* Working solo on a branch

> 🚨 **Never rebase shared branches.**

---

## 🧹 Squash Commits

### What Is Squashing?

Combining multiple small commits into **one meaningful commit**.

Example:

```text
Before:
fix typo
fix typo again
update readme
final fix

After Squash:
Add README usage section
```

### Why Squash?

* Removes noise
* Improves readability
* One commit = one logical change

### How Squash Is Done (PR Level)

GitHub allows:

* **Squash and merge**
* Keeps `main` history clean

> ✅ Recommended for most feature branches.

---

## ✍️ Rewriting History Responsibly

Rewriting history includes:

* Rebase
* Reset
* Amend commits

### Allowed When:

* Working on local branches
* Feature branch not yet shared
* Fixing mistakes before PR

### Dangerous When:

* Branch is already pushed and used by others
* Code exists in production

> 🔴 **Golden Rule:**
> Never rewrite history that others depend on.

---

## 🧪 Hands-On Lab

---

## 🧩 Exercise 1 – Rebase Flow

### Step 1: Switch to Feature Branch

```bash
git checkout feature/add-readme-section
```

---

### Step 2: Rebase on `main`

```bash
git rebase main
```

📌 Purpose:
Bring your feature branch up to date with the latest production code.

---

### Step 3: Resolve Conflicts (If Any)

If Git reports conflicts:

```bash
git status
```

* Open conflicted files
* Fix conflicts manually
* Mark as resolved:

```bash
git add <file>
git rebase --continue
```

---

### 🧠 Learning Outcome

* Conflicts are resolved **once**
* History stays linear
* Cleaner PR diff

---

## 🧩 Exercise 2 – Reset (Safe Practice)

---

### 🔹 Soft Reset

```bash
git reset --soft HEAD~1
```

**What it does:**

* Removes last commit
* Keeps changes staged

**Use when:**

* Commit message is wrong
* Want to combine commits

---

### 🔹 Hard Reset

```bash
git reset --hard HEAD~1
```

**What it does:**

* Deletes last commit
* Deletes changes completely

**Use when:**

* Experiment went wrong
* You want to discard changes entirely

> ⚠️ **Hard reset permanently deletes work.**

---

## 📌 Comparison Summary

| Command  | Affects History | Keeps Changes | Risk Level |
| -------- | --------------- | ------------- | ---------- |
| `--soft` | Yes             | Yes (staged)  | Low        |
| `--hard` | Yes             | No            | High       |

---

## 📄 Documentation Section

---

## 🚫 When NOT to Rewrite History

### Do NOT Rewrite History When:

1. Branch is already pushed to remote
2. Branch is shared with teammates
3. Code has been merged into `main`
4. Commit is part of production release
5. CI/CD pipelines rely on commit SHA

### Why?

* Breaks teammate branches
* Causes merge conflicts
* Invalidates audit logs
* Damages trust in repo history

> ❗ **In teams, broken history is worse than messy history.**

---

## ✅ Key Takeaways

* Merge = safe, verbose history
* Rebase = clean, dangerous if misused
* Squash = clarity and professionalism
* Reset is powerful — use carefully
* History is a contract with your team

---

📌 *This module reflects enterprise Git standards followed by mature DevOps teams.*

➡️ **Next Module:**
Tagging, Releases & Semantic Versioning

```
```

