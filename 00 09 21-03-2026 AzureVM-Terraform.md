# 🚀 Terraform Azure VM Deployment (End-to-End)

**Author:** Atul Kamble
**Role:** Cloud Solutions Architect | DevOps Trainer

---

# 📌 Project Overview

This Terraform project provisions a **complete Azure infrastructure** including:

* ✅ Resource Group
* ✅ Virtual Network (VNet)
* ✅ Subnet
* ✅ Network Interface (NIC)
* ✅ Linux Virtual Machine (Ubuntu 22.04)

---

# 🏗️ Architecture Flow

```
Resource Group
   ↓
Virtual Network (10.0.0.0/16)
   ↓
Subnet (10.0.1.0/24)
   ↓
Network Interface
   ↓
Linux Virtual Machine (Ubuntu 22.04)
```

---

# ⚙️ Provider Configuration

```hcl
terraform {
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = "4.65.0"
    }
  }
}

provider "azurerm" {
  features {}
  subscription_id = "08b7b8d4-af42-4972-9517-11ea256ea068"
}
```

### 🔹 Explanation

| Component         | Description                            |
| ----------------- | -------------------------------------- |
| `azurerm`         | Azure Resource Manager provider        |
| `version`         | Provider version for stability         |
| `subscription_id` | Azure subscription used for deployment |

---

# 📦 Resource Group

```hcl
resource "azurerm_resource_group" "my_rg" {
  name     = "myResourceGroup"
  location = "East US"
}
```

### 🔹 Purpose

* Logical container for all Azure resources
* Defines deployment region

---

# 🌐 Virtual Network (VNet)

```hcl
resource "azurerm_virtual_network" "my_vnet" {
  name                = "myVnet"
  address_space       = ["10.0.0.0/16"]
  resource_group_name = azurerm_resource_group.my_rg.name
  location            = azurerm_resource_group.my_rg.location
}
```

### 🔹 Key Points

* CIDR: `10.0.0.0/16`
* Provides isolated network environment

---

# 🔌 Subnet

```hcl
resource "azurerm_subnet" "my_subnet" {
  name                 = "mySubnet"
  resource_group_name  = azurerm_resource_group.my_rg.name
  virtual_network_name = azurerm_virtual_network.my_vnet.name
  address_prefixes     = ["10.0.1.0/24"]
}
```

### 🔹 Key Points

* Subnet range: `10.0.1.0/24`
* Used to host VM resources

---

# 🖧 Network Interface (NIC)

```hcl
resource "azurerm_network_interface" "my_nic" {
  name                = "myNic"
  location            = azurerm_resource_group.my_rg.location
  resource_group_name = azurerm_resource_group.my_rg.name

  ip_configuration {
    name                          = "myIpConfig"
    subnet_id                     = azurerm_subnet.my_subnet.id
    private_ip_address_allocation = "Dynamic"
  }
}
```

### 🔹 Key Points

* Connects VM to subnet
* Uses **dynamic private IP allocation**

---

# 🖥️ Linux Virtual Machine

```hcl
resource "azurerm_linux_virtual_machine" "myvm" {
  name                  = "myVM"
  resource_group_name   = azurerm_resource_group.my_rg.name
  location              = azurerm_resource_group.my_rg.location
  size                  = "Standard_L2aos_V4"
  admin_username        = "azureuser"
  disable_password_authentication = false
  admin_password        = "P@ssw0rd1234!"
  
  network_interface_ids = [
    azurerm_network_interface.my_nic.id,
  ]

  os_disk {
    name                 = "myosDisk"
    caching              = "ReadWrite"
    storage_account_type = "Standard_LRS"
  }

  source_image_reference {
    publisher = "Canonical"
    offer     = "0001-com-ubuntu-server-jammy"
    sku       = "22_04-lts-gen2"
    version   = "latest"
  }

  admin_ssh_key {
    username   = "azureuser"
    public_key = file("~/.ssh/id_rsa.pub")
  }
}
```

---

# 🔑 VM Configuration Highlights

| Setting        | Value                  |
| -------------- | ---------------------- |
| OS             | Ubuntu 22.04 LTS       |
| Size           | Standard_L2aos_V4      |
| Authentication | Password + SSH Key     |
| Disk Type      | Standard_LRS           |
| IP             | Private (No Public IP) |

---

# ⚠️ Important Notes (VERY IMPORTANT FOR EXAMS + REAL WORLD)

* ❌ No Public IP → VM is **not accessible from internet**
* ⚠️ Password auth enabled → **Not recommended for production**
* 🔐 Hardcoded password → Use **Key Vault or variables**
* 🔑 SSH key file must exist locally (`~/.ssh/id_rsa.pub`)

---

# 🚀 Deployment Commands

```bash
terraform init -upgrade
terraform plan
terraform apply -auto-approve
```

---

# 🧹 Destroy Infrastructure

```bash
terraform destroy
```

---

# 🧠 Best Practices (Architect Level)

✅ Use **variables.tf** for dynamic values
✅ Store secrets in **Azure Key Vault**
✅ Enable **NSG (Network Security Group)**
✅ Add **Public IP only if required**
✅ Use **Managed Identity instead of passwords**
✅ Use **Terraform backend (remote state)**

---

# 📊 Interview / Viva Questions

* What is the difference between VNet and Subnet?
* Why NIC is required for VM?
* Difference between SSH and Password authentication?
* What happens if no Public IP is assigned?
* Why use Terraform over ARM/Bicep?

---

# 🎯 Summary

This project demonstrates:

* Full Azure infrastructure provisioning
* Networking + Compute integration
* Secure VM deployment basics
* Real-world Terraform workflow

---
