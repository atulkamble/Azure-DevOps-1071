# 🚀 Jenkins Installation & Configuration on Azure VM (Ubuntu)

**Author:** Atul Kamble
**Role:** Cloud Solutions Architect | DevOps Trainer

---

# 🖥️ 1️⃣ Infrastructure Setup (Azure VM)

| Component      | Value             |
| -------------- | ----------------- |
| Cloud Provider | Azure             |
| OS             | Ubuntu Linux      |
| Disk           | 128 GB SSD        |
| Access         | SSH (key.pem)     |
| Port           | 8080 (Jenkins UI) |

### 🔐 Network Security Group (NSG)

Allow inbound traffic:

| Port | Protocol | Purpose    |
| ---- | -------- | ---------- |
| 22   | TCP      | SSH Access |
| 8080 | TCP      | Jenkins UI |

---

# 🔑 2️⃣ Connect to VM

```bash
cd Downloads
chmod 400 key.pem
ssh -i key.pem atul@20.109.50.38
```

---

# 🔄 3️⃣ System Update

```bash
sudo apt update -y
sudo apt list --upgradable
sudo apt upgrade -y
```

---

# 🧰 4️⃣ Install Required Tools

```bash
sudo apt install git docker.io tree python-is-python3 -y
```

### 🔧 Configure Git

```bash
git config --global user.name "Atul Kamble"
git config --global user.email "atul_kamble@hotmail.com"
git config --list
```

### 🐳 Enable Docker

```bash
sudo systemctl enable docker
sudo systemctl start docker
```

---

# ☕ 5️⃣ Install Java (Jenkins Requirement)

```bash
sudo apt install openjdk-21-jdk -y
java --version
```

---

# ⚙️ 6️⃣ Install Jenkins

### ➤ Add Jenkins Repository

```bash
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key

echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null
```

### ➤ Install Jenkins

```bash
sudo apt update
sudo apt install jenkins
```

---

# ▶️ 7️⃣ Start Jenkins Service

```bash
jenkins --version
sudo systemctl enable jenkins
sudo systemctl start jenkins
```

---

# 🌐 8️⃣ Access Jenkins UI

Open browser:

```
http://20.109.50.38:8080
```

---

# 🔐 9️⃣ Get Initial Admin Password

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

---

# 🔌 🔟 Install Required Plugins

Go to:

**Manage Jenkins → Plugins**

### Recommended Plugins:

* ✅ Blue Ocean
* ✅ Docker
* ✅ Docker Pipeline

---

# 🛠️ 1️⃣1️⃣ Configure Global Tools

Go to:

**Manage Jenkins → Tools**

Configure:

| Tool   | Name     | Option                |
| ------ | -------- | --------------------- |
| Git    | myGit    | Install automatically |
| Docker | myDocker | Install automatically |

---

# 🐳 1️⃣2️⃣ Enable Docker for Jenkins

```bash
sudo usermod -aG docker jenkins
sudo systemctl restart jenkins
```

---

# 🔁 1️⃣3️⃣ Create First Pipeline

### Steps:

1. Click **New Item**
2. Enter name → `mypipeline`
3. Select **Pipeline**
4. Click **OK**
5. Choose **Hello World Pipeline**
6. Click **Build Now**
7. Check **Console Output**

---

# 📜 Sample Jenkins Pipeline

```groovy
pipeline {
    agent any

    stages {
        stage('dev') {
            steps {
                echo 'I am in dev'
                sh 'git --version'
            }
        }
    }
}
```

---

# 📊 1️⃣4️⃣ Validation Checklist

| Check              | Command / Action           |
| ------------------ | -------------------------- |
| Java Installed     | `java --version`           |
| Jenkins Running    | `systemctl status jenkins` |
| Docker Running     | `systemctl status docker`  |
| Jenkins UI         | Browser :8080              |
| Pipeline Execution | Console Output             |

---

# ⚠️ Troubleshooting Tips

### ❌ Jenkins not opening

```bash
sudo systemctl status jenkins
sudo journalctl -u jenkins
```

### ❌ Port issue

* Check NSG rules (8080 open)

### ❌ Docker permission issue

```bash
sudo usermod -aG docker jenkins
sudo systemctl restart jenkins
```

---

# 🎯 Key Learning Outcomes

* ✅ Jenkins installation on Ubuntu VM
* ✅ Java + Docker integration
* ✅ Plugin & tool configuration
* ✅ Pipeline creation (CI basics)
* ✅ Real DevOps environment setup

---

# 🚀 Next Steps (Advanced)

* 🔹 Integrate GitHub Webhooks
* 🔹 Build Docker Image in Pipeline
* 🔹 Deploy to Kubernetes (AKS/EKS)
* 🔹 Add SonarQube Code Quality
* 🔹 Implement CI/CD End-to-End

---
