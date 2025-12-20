## 📌 Git, VCS & SCM – Key Concepts (Refined Notes)

### 1️⃣ Git Never Tracks Empty Directories
Git does **not track empty folders** by design.  
A directory is tracked only when it contains at least one file.  
Common workaround: add a `.gitkeep` or `.gitignore` file.

---

### 2️⃣ Simple Analogy: VCS vs SCM
**VCS is the engine**, responsible for tracking versions of code.  
**SCM is the full vehicle** — engine + controls + safety + process.  
SCM includes policies, workflows, reviews, and releases.

---

### 3️⃣ VCS vs SCM – Core Difference
**VCS tracks code changes** over time (commits, diffs, history).  
**SCM manages how code is developed, reviewed, tested, and released**.  
SCM is broader and process-oriented.

---

### 4️⃣ Git
Git is a **tool**.  
It is a **Version Control System (VCS)** used to track source code changes locally and remotely.

---

### 5️⃣ GitHub
GitHub is a **platform**.  
It provides **SCM capabilities** like PRs, reviews, CI/CD, issues, and collaboration on top of Git.

---

### 6️⃣ SCM (Source Code Management)
SCM is a **discipline/process**, not just a tool.  
It defines **how teams collaborate**, enforce standards, and release software safely.

---

### 7️⃣ VCS (Version Control System)
VCS is a **version tracking system**.  
It records who changed what, when, and why, enabling rollback and collaboration.

---

## 🔗 Git Submodules – Key Points to Remember

### 8️⃣ What Are Submodules?
A Git submodule is a **separate Git repository inside another repository**.  
It allows you to reuse external projects while keeping histories separate.

---

### 9️⃣ How Submodules Are Tracked
The parent repository tracks a **specific commit** of the submodule,  
not the branch, by default.

---

### 🔄 Updating Submodules
After cloning or pulling changes, **submodules must be updated manually**.  
Use `git submodule update --init --recursive`.

---

### 🌳 Nested Submodules
Submodules can contain **other submodules**.  
Use the `--recursive` flag to clone or update all levels.

---

### 📁 Visual Concept

ParentRepo/
│

├── main_code/

├── libs/

│   └── library/← Submodule (separate Git repo)

└── README.md

The parent repo only stores **which commit** of `library` it uses.

---

### 💡 When to Use Submodules
Submodules are ideal for **shared libraries across multiple projects**.  
For simpler workflows, **Git subtree or copying code** may be easier.

---

## ⚠️ Common Error Faced

### Rebasing Error: Different Branch Histories
This error occurs when **branches have unrelated or divergent histories**.  
It usually happens after force pushes, rebasing shared branches, or independent repo initialization.

---

### .gitignore is a file not a directory 
I initialized it as a directory due to which it was not tracked on Github.

