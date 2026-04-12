# 🚀 Azure Web App Deployment using GitHub Actions (Node.js)

## 📌 Project Overview

This project demonstrates how to deploy a **Node.js Web App** to **Azure App Service** using **GitHub Actions CI/CD pipeline**.

---

## 🧰 Prerequisites

* Azure Account
* GitHub Account
* Node.js installed
* VS Code
* Basic knowledge of Git

---

## 📂 Step 1: Fork Repository

Fork the repo:

👉 [https://github.com/atulkamble/azure-pipeline-nodejs-webapp](https://github.com/atulkamble/azure-pipeline-nodejs-webapp)

---

## 💻 Step 2: Clone Repository

```bash
git clone https://github.com/your-username/azure-pipeline-nodejs-webapp.git
cd azure-pipeline-nodejs-webapp
git pull
```

---

## 🧑‍💻 Step 3: Run Application Locally

```bash
npm install express
node index.js
```

Open browser:

👉 [http://localhost:3000](http://localhost:3000)

---

## ☁️ Step 4: Create Azure Web App

1. Go to **Azure Portal**
2. Create **App Service (Web App)**
3. Select:

   * Runtime: Node.js
   * Region: Any (e.g., Canada Central)
4. After creation:

   * Go to **Deployment Center**

---

## 🔁 Step 5: Configure GitHub Actions

Inside **Deployment Center**:

1. Select **Source → GitHub**
2. Authorize GitHub
3. Select:

   * Repository: `azure-pipeline-nodejs-webapp`
   * Branch: `main`
4. Click **Save**

👉 Azure will automatically:

* Create a **GitHub Actions workflow**
* Setup CI/CD pipeline

---

## 🔐 Step 6: Add Service Connection (IMPORTANT)

In GitHub Repository:

1. Go to **Settings → Secrets and variables → Actions**
2. Add secret:

```
Name: AZURE_CREDENTIALS
```

3. Value: (From Azure Service Principal)

```bash
az ad sp create-for-rbac \
  --name "github-action-sp" \
  --role contributor \
  --scopes /subscriptions/<subscription-id> \
  --sdk-auth
```

---

## 🔗 Service Connection Name

```yaml
azure-subscription
```

(Used inside workflow YAML)

---

## 🔄 Step 7: Trigger Deployment

Make any code change:

```bash
git add .
git commit -m "update"
git push
```

---

## 🌐 Step 8: Access Deployed App

👉 [https://atulkamble-d9excbfdhjc8fza9.canadacentral-01.azurewebsites.net/](https://atulkamble-d9excbfdhjc8fza9.canadacentral-01.azurewebsites.net/)

---

## ⚙️ GitHub Actions Workflow (Sample)

```yaml
name: Build and deploy Node.js app to Azure Web App

on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'

      - name: Install dependencies
        run: npm install

      - name: Deploy to Azure Web App
        uses: azure/webapps-deploy@v2
        with:
          app-name: <your-app-name>
          publish-profile: ${{ secrets.AZURE_WEBAPP_PUBLISH_PROFILE }}
```

---

## 📊 Flow Diagram

```
Developer → GitHub Repo → GitHub Actions → Azure Web App → Live URL
```

---

## 🧠 Points to Remember

* Deployment Center auto-generates GitHub workflow
* Always store credentials in **GitHub Secrets**
* Use **Publish Profile OR Service Principal**
* Every push → triggers automatic deployment
* Ensure correct **app-name** in workflow

---

## 📌 Interview Questions

1. What is GitHub Actions in Azure deployment?
2. Difference between Publish Profile and Service Principal?
3. What is Deployment Center in Azure?
4. How CI/CD works for Web Apps?
5. How to secure credentials in GitHub Actions?

---
