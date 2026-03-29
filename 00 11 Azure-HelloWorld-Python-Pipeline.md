# 🚀 Azure Pipeline – Python Hello World

## 📌 Project Overview

This project demonstrates a **basic Azure DevOps Pipeline** that runs a simple Python script using a Microsoft-hosted agent.

It is designed for **beginners** to understand:

* Azure Pipelines YAML structure
* CI trigger configuration
* Running scripts in pipeline agents

```
trigger:
- main

pool:
  vmImage: 'ubuntu-latest'

steps:
- script: |
    echo "Installing Python 3.8"
    sudo apt-get update
    sudo apt-get install python3 -y 
    python3 --version
    python3 helloworld.py  
  displayName: 'Run Python Script' 

```

---

## 🏗️ Architecture (Flow)

```
GitHub Repo (main branch)
        ↓
Azure DevOps Pipeline Trigger
        ↓
Hosted Agent (ubuntu-latest)
        ↓
Install Python + Execute Script
        ↓
Output in Pipeline Logs
```

---

## 📂 Project Structure

```
.
├── azure-pipelines.yml   # Pipeline definition
├── helloworld.py         # Python script
├── README.md             # Documentation
└── LICENSE               # License file
```

---

## ⚙️ Pipeline Configuration

### 📄 azure-pipelines.yml

```yaml
trigger:
- main

pool:
  vmImage: 'ubuntu-latest'

steps:
- script: |
    echo "Installing Python 3.8"
    sudo apt-get update
    sudo apt-get install python3 -y 
    python3 --version
    python3 helloworld.py  
  displayName: 'Run Python Script'
```

---

## 🔍 Explanation (Line by Line)

### 🔹 Trigger

```yaml
trigger:
- main
```

* Pipeline runs automatically on every push to **main branch**

---

### 🔹 Agent Pool

```yaml
pool:
  vmImage: 'ubuntu-latest'
```

* Uses Microsoft-hosted Linux agent
* No manual setup required

---

### 🔹 Steps Section

```yaml
steps:
```

Defines tasks executed in pipeline

---

### 🔹 Script Execution

```yaml
- script: |
```

Runs shell commands inside agent

Commands executed:

* Update packages
* Install Python
* Check version
* Run Python script

---

### 🔹 Display Name

```yaml
displayName: 'Run Python Script'
```

* Name shown in pipeline UI

---

## 🐍 Python Script

### 📄 helloworld.py

```python
print("Hello, Azure DevOps Pipeline!")
```

---

## ▶️ How to Run This Project

### Step 1: Push Code to GitHub

Repo:
👉 [https://github.com/atulkamble/new-azure-pipeline](https://github.com/atulkamble/new-azure-pipeline)

---

### Step 2: Create Azure DevOps Pipeline

1. Go to **Azure DevOps**
2. Navigate to **Pipelines**
3. Click **New Pipeline**
4. Select **GitHub**
5. Choose your repo
6. Select **Existing YAML file**
7. Select `azure-pipelines.yml`

---

### Step 3: Run Pipeline

* Click **Run Pipeline**
* Monitor execution logs

---

## 📊 Expected Output

```
Installing Python 3.8
Python 3.x.x
Hello, Azure DevOps Pipeline!
```

---

## ✅ Key Learning Points

* YAML-based pipeline configuration
* CI trigger using GitHub
* Using hosted agents
* Running scripts in pipeline
* Basic DevOps automation

---

## 🚀 Improvements (Next Steps)

* Add **requirements.txt** for dependencies
* Use **Python task instead of script**
* Add **test stage (pytest)**
* Integrate **CI/CD (deploy to Azure App Service / VM)**
* Add **multi-stage pipeline**

---

## 🏁 Conclusion

This project provides a **minimal working Azure Pipeline** to understand:

* Pipeline execution flow
* YAML basics
* Script automation

Perfect starting point for **AZ-400 / DevOps beginners**

---
