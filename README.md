# Azure-DevOps-1071
# 🖥️ Windows DevOps & Cloud Setup Guide (Step-by-Step)

This guide helps you set up a **complete Cloud & DevOps development environment** on Windows.

---

## 1️⃣ Run PowerShell as Administrator

Before installing tools:

* Click **Start**
* Search for **PowerShell**
* Right-click → **Run as Administrator**

---

## 2️⃣ Install WSL (Windows Subsystem for Linux)

```powershell
wsl --install
```

* Restart your system after installation
* Verify installation:

```powershell
wsl --status
```

---

## 3️⃣ Install Chocolatey (Windows Package Manager)

🔗 [https://chocolatey.org/install](https://chocolatey.org/install)

Run the installation command in **Admin PowerShell** as given on the website.

Verify:

```powershell
choco -v
```

---

## 4️⃣ Install Visual Studio Code (VS Code)

🔗 [https://code.visualstudio.com/](https://code.visualstudio.com/)

* Download Windows installer
* Install with default settings
* Recommended Extensions:

  * Azure Tools
  * Docker
  * Kubernetes
  * Python
  * GitLens

---

## 5️⃣ Install PowerShell 7 (Latest)

🔗 [https://learn.microsoft.com/en-us/powershell/scripting/install/install-powershell-on-windows?view=powershell-7.5#install-the-msi-package](https://learn.microsoft.com/en-us/powershell/scripting/install/install-powershell-on-windows?view=powershell-7.5#install-the-msi-package)

* Download MSI package
* Install and verify:

```powershell
pwsh
$PSVersionTable
```

---

## 6️⃣ Install Azure CLI

🔗 [https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows?view=azure-cli-latest&pivots=msi](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows?view=azure-cli-latest&pivots=msi)

Download and install MSI.

Verify:

```powershell
az version
```

Login:

```powershell
az login
```

---

## 7️⃣ Install Python

🔗 [https://www.python.org/downloads/](https://www.python.org/downloads/)

* Download latest version
* ✅ Check **"Add Python to PATH"** during installation

Verify:

```powershell
python --version
pip --version
```

---

## 8️⃣ Install Node.js

🔗 [https://nodejs.org/en/download](https://nodejs.org/en/download)

* Download LTS version
* Install with default settings

Verify:

```powershell
node -v
npm -v
```

---

## 9️⃣ Install Java 21 (JDK)

🔗 [https://www.oracle.com/java/technologies/javase/jdk21-archive-downloads.html](https://www.oracle.com/java/technologies/javase/jdk21-archive-downloads.html)

* Download **Windows x64 MSI Installer**
* Install and verify:

```powershell
java -version
javac -version
```

---

## 🔟 Install Git

🔗 [https://git-scm.com/install/windows](https://git-scm.com/install/windows)

* Install with default settings
* Verify:

```powershell
git --version
```

Configure:

```powershell
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

---

## 1️⃣1️⃣ Install Docker Desktop

🔗 [https://docs.docker.com/desktop/setup/install/windows-install/](https://docs.docker.com/desktop/setup/install/windows-install/)

* Install Docker Desktop
* Enable WSL 2 backend
* Restart system

Verify:

```powershell
docker --version
docker run hello-world
```

---

## 1️⃣2️⃣ Install Jenkins

🔗 [https://www.jenkins.io/download/](https://www.jenkins.io/download/)

### Steps:

1. Download Windows installer
2. Install (Java must be installed first)
3. Access in browser:

```
http://localhost:8080
```

4. Unlock Jenkins using initial admin password from:

```
C:\Program Files\Jenkins\secrets\initialAdminPassword
```

---

# ✅ Final Verification Checklist

Run these commands to confirm everything is working:

```powershell
wsl --status
choco -v
code --version
az version
python --version
node -v
java -version
git --version
docker --version
```

---

# 🎯 Recommended for Cloud & DevOps Learning

This setup supports:

* ☁️ Azure & Cloud CLI
* 🐳 Docker Containers
* 🔁 CI/CD with Jenkins
* 💻 Full Stack Development
* 🧑‍💻 Infrastructure Automation

---
