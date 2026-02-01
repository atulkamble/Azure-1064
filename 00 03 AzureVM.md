# ☁️ Azure CLI — Resource Group & VM Management Guide

This document demonstrates how to use **Azure CLI (`az`)** to manage **Resource Groups** and **Virtual Machines (Linux & Windows)**.

---

## 🔧 Prerequisites

* Azure Subscription
* Azure CLI installed
  👉 `az --version`
* Internet access
* Valid Azure credentials

---

## 🔐 Azure Login

```bash
az login
```

Opens a browser window to authenticate with Azure.

---

## 📍 List Available Azure Locations

```bash
az account list-locations
```

Displays all regions available for your subscription.

---

## 📦 Resource Group Management

### ➕ Create Resource Group (Multiline)

```bash
az group create \
  --name myRG \
  --location eastus
```

### ➕ Create Resource Group (Single Line)

```bash
az group create --name myRG --location eastus
```

### 📄 List Resource Groups

```bash
az group list
```

### ❌ Delete Resource Group (Prompt Confirmation)

```bash
az group delete --name myRG
```

### ❌ Delete Resource Group (No Prompt, Async)

```bash
az group delete --name myRG --yes --no-wait
```

---

## 🖥️ Virtual Machine (Linux – Password Authentication)

### ➕ Create Ubuntu VM (Multiline)

```bash
az vm create \
  --resource-group myRG \
  --name myVM \
  --image Ubuntu2204 \
  --size Standard_B1s \
  --admin-username atul \
  --admin-password 'Password@123' \
  --authentication-type password \
  --public-ip-sku Standard \
  --os-disk-size-gb 30
```

### ➕ Create Ubuntu VM (Single Line)

```bash
az vm create --resource-group myRG --name myVM --image Ubuntu2204 --size Standard_B1s --admin-username atul --admin-password 'Password@123' --authentication-type password --public-ip-sku Standard --os-disk-size-gb 30
```

---

## 🖥️ Virtual Machine (Linux – SSH Key Authentication)

```bash
az vm create \
  --resource-group myRG \
  --name MyVm \
  --image UbuntuLTS \
  --admin-username azureuser \
  --generate-ssh-keys
```

✔️ Automatically generates SSH keys if not present.

---

## 🔓 Open Network Ports

### 🔑 Open SSH Port (22)

```bash
az vm open-port \
  --resource-group myRG \
  --name myVM \
  --port 22
```

### 🖥️ Open RDP Port (3389 – Windows)

```bash
az vm open-port \
  --resource-group myRG \
  --name myVM \
  --port 3389
```

---

## 🔐 Connect to Linux VM (SSH)

```bash
ssh atul@20.69.108.26
```

> Replace IP with your VM’s public IP.

---

## 🧠 VM Reference & Discovery Commands

### 📏 List VM Sizes

```bash
az vm list-sizes
```

### 🧾 List VM SKUs

```bash
az vm list-skus
```

### ❓ Azure VM Help

```bash
az vm --help
```

---

## 🖥️ Create Linux VM (Custom Resource Group)

```bash
az vm create \
  --resource-group RG_by_cli \
  --name VMbycli \
  --image Ubuntu2204 \
  --size Standard_D2s_v3 \
  --admin-username siddhesh09 \
  --admin-password 'Siddhesh@123' \
  --authentication-type password \
  --public-ip-sku Standard \
  --os-disk-size-gb 30
```

---

## 🪟 Virtual Machine (Windows Server 2022)

### ➕ Create Windows VM

```bash
az vm create \
  --resource-group myRG \
  --name myVM \
  --image Win2022Datacenter \
  --size Standard_B2s \
  --admin-username azureadmin \
  --admin-password 'Password@123' \
  --public-ip-sku Standard \
  --os-disk-size-gb 127
```

### 🔓 Open RDP Port

```bash
az vm open-port \
  --resource-group myRG \
  --name myVM \
  --port 3389
```

---

## ⚠️ Security Best Practices (Important)

* ❌ Avoid hardcoding passwords in production
* ✅ Prefer **SSH keys** for Linux VMs
* ✅ Use **Azure Key Vault** for secrets
* ✅ Restrict NSG rules (don’t open ports to `0.0.0.0/0`)
* ✅ Stop or delete unused VMs to save cost

---

## ✅ Summary

This guide covered:

* Azure login & region discovery
* Resource Group lifecycle
* Linux & Windows VM creation
* Password vs SSH authentication
* Network port management
* VM reference commands

---
