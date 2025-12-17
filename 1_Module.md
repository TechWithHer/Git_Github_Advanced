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
that enforces code quality, automates testing, and enables
continuous delivery using GitHub Actions.
s a **product**, not just fil

