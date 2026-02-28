# Git & Azure Repos – Complete Step-by-Step Documentation

---

# Part 1: GitHub Repository – Clone, Branch & Push

## 1️⃣ Configure Git (One Time Setup)

```bash
git config --global user.name "Atul Kamble"
git config --global user.email "atul_kamble@hotmail.com"
git config --list
```

✔ Sets global username and email
✔ `git config --list` verifies configuration

---

## 2️⃣ Clone Repository from GitHub

```bash
git clone https://github.com/atulkamble/myrepo.git
cd myrepo
```

👉 Enter your GitHub username when prompted.

---

## 3️⃣ Create New Branch & Push Code

```bash
git branch atul
git checkout atul
touch atul.txt
nano atul.txt
git add atul.txt
git commit -m "atul"
git push origin atul
```

✔ Creates new branch
✔ Adds file
✔ Commits changes
✔ Pushes branch to remote

---

## 4️⃣ List All Branches

```bash
git branch -a
```

✔ Shows local + remote branches

---

# Part 2: Azure Repos – Create & Maintain Repository

## 🔹 Step 1: Create Azure DevOps Organization

Visit:
👉 [https://dev.azure.com](https://dev.azure.com)

Create Organization:

```
atul-kamble
```

---

## 🔹 Step 2: Create Project

Project Name:

```
project
```

Example URL:

```
https://dev.azure.com/atul-kamble/project
```

Azure Repos Product Page:
Azure DevOps

Official Git Documentation:
Microsoft Learn

---

## 🔹 Step 3: Create Personal Access Token (PAT)

Azure DevOps → User Settings → Personal Access Token

✔ Select Full Access
✔ Copy Token

⚠️ Never expose PAT publicly.

---

## 🔹 Step 4: Clone Azure Repo

```bash
git clone https://atul-kamble@dev.azure.com/atul-kamble/project/_git/project
cd project
```

---

## 🔹 Step 5: Add & Push Code

```bash
echo "hello world" >> hello.txt
git add hello.txt
git commit -m "code"
git push origin main
```

👉 When prompted:

* Username → your Azure DevOps username
* Password → Paste PAT token

---

## 🔹 Step 6: Create Branch & Push

```bash
git branch
git branch prod
git checkout prod
git push origin prod
```

---

## 🔹 Step 7: Create Tag & Push

```bash
git tag 1.0.1
git push origin --tags
```

✔ Useful for versioning releases

---

# Useful References

Git Cheat Sheet:
GitHub Education

Azure Repos Documentation:
[https://learn.microsoft.com/en-us/azure/devops/repos/git/?view=azure-devops](https://learn.microsoft.com/en-us/azure/devops/repos/git/?view=azure-devops)

---

# 🔥 Summary

✔ Configure Git
✔ Clone Repository
✔ Create Branch
✔ Commit & Push
✔ Create Azure DevOps Org & Project
✔ Generate PAT
✔ Push Code to Azure Repos
✔ Manage Branches & Tags

---
