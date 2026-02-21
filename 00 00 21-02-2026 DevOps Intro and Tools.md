# 🚀 DevOps Notes (Azure-Focused)

## 🔹 What is DevOps?

**DevOps = Development + Operations**

DevOps is a **set of practices, culture, and tools** that integrates software development (Dev) and IT operations (Ops) to:

* Deliver applications faster
* Improve collaboration
* Automate workflows
* Ensure reliability & scalability

---

# 🔧 Core DevOps Practices

### 1️⃣ Automation

* CI/CD pipelines
* Infrastructure provisioning
* Testing & deployments

### 2️⃣ Version Control

* Track code changes
* Collaboration & branching strategy

### 3️⃣ Containerization

* Package applications with dependencies
* Portable & consistent environments

### 4️⃣ Infrastructure Deployment

* Infrastructure as Code (IaC)
* Automated provisioning

---

# 🛠 DevOps Tools Mapping (General ➜ Azure Equivalent)

| Category                 | Tool       | Azure Equivalent                                      |
| ------------------------ | ---------- | ----------------------------------------------------- |
| Version Control          | Git        | Azure Repos                                           |
| CI/CD                    | Jenkins    | Azure Pipelines (Azure DevOps)                        |
| Containerization         | Docker     | Azure Container Instances (ACI), Azure Container Apps |
| Container Orchestration  | Kubernetes | Azure Kubernetes Service (AKS)                        |
| Configuration Management | Ansible    | Azure Automation                                      |
| Configuration Management | Chef       | Azure VM Extensions                                   |
| Configuration Management | Puppet     | Azure Automation DSC                                  |
| Monitoring               | Grafana    | Azure Monitor                                         |
| Monitoring               | Prometheus | Azure Monitor + Managed Prometheus                    |
| Infrastructure as Code   | Terraform  | ARM Templates, Bicep                                  |

---

# ☁️ Azure – Basic Concepts

Azure is Microsoft’s **Cloud Computing Platform** offering:

* Compute (VM, AKS, App Service)
* Storage (Blob, Disk, File)
* Networking (VNet, Load Balancer)
* Databases (Azure SQL, Cosmos DB)
* DevOps (Azure DevOps Services)

---

# 🏢 Azure Organization Structure

```
Management Group
    ↓
Subscription
    ↓
Resource Group
    ↓
Resources (VM, AKS, Storage, etc.)
```

---

# 🔵 Create Azure DevOps Organization

## Step 1: Login

👉 [https://portal.azure.com](https://portal.azure.com)

## Step 2: Search

Search: **Azure DevOps**

## Step 3: Create Organization

Organization Name:

```
atul-kamble
```

## Step 4: Create Project

Project Name:

```
project
```

## Project URL:

```
https://dev.azure.com/atul-kamble/project
```

---

# 🔁 Sign up for Azure Pipelines Parallelism

Request parallel jobs:

👉 [https://aka.ms/azpipelines-parallelism-request](https://aka.ms/azpipelines-parallelism-request)

Mention your Project URL:

```
https://dev.azure.com/atul-kamble/project
```

---

# 🔀 Fork GitHub Repository

Fork this repo:

```
https://github.com/atulkamble/azure-pipeline-test
```

---

# 💻 Windows Setup (Run PowerShell as Administrator)

## Install WSL

```powershell
wsl --install
```

---

## Install Chocolatey

👉 [https://chocolatey.org/install](https://chocolatey.org/install)

---

# 🧰 Required Tools Installation

### VS Code

[https://code.visualstudio.com/](https://code.visualstudio.com/)

### PowerShell 7

[https://learn.microsoft.com/en-us/powershell/scripting/install/install-powershell-on-windows](https://learn.microsoft.com/en-us/powershell/scripting/install/install-powershell-on-windows)

### Azure CLI

[https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows)

### Python

[https://www.python.org/downloads/](https://www.python.org/downloads/)

### NodeJS

[https://nodejs.org/en/download](https://nodejs.org/en/download)

### Java 21 (MSI)

[https://www.oracle.com/java/technologies/javase/jdk21-archive-downloads.html](https://www.oracle.com/java/technologies/javase/jdk21-archive-downloads.html)

### Git

[https://git-scm.com/install/windows](https://git-scm.com/install/windows)

### Docker Desktop

[https://docs.docker.com/desktop/setup/install/windows-install/](https://docs.docker.com/desktop/setup/install/windows-install/)

### Jenkins

[https://www.jenkins.io/download/](https://www.jenkins.io/download/)

---

# 🧩 Recommended VS Code Extensions

* GitHub Copilot
* Docker
* Docker DX
* Kubernetes (Microsoft)
* Azure Pipelines
* Azure Container Apps
* HashiCorp Terraform
* Microsoft Terraform

---

# 📌 Summary Flow (DevOps on Azure)

```
Developer → Git (Azure Repos)
          → Azure Pipeline (CI/CD)
          → Docker Build
          → Push to ACR
          → Deploy to AKS / Azure App Service
          → Monitor using Azure Monitor / Grafana
          → Infrastructure via Terraform / Bicep
```

---
