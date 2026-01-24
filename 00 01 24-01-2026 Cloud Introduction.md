# ☁️ Cloud Computing – Fundamentals (Well-Documented Notes)

---

## 🌩️ What is Cloud Computing?

**Cloud Computing** is the **on-demand delivery of IT resources** such as compute, storage, networking, and databases **over the internet**, with **pay-as-you-go pricing**.

### ✅ Key Characteristics

* On-demand self-service
* Scalability & elasticity
* High availability
* Global access
* Pay only for what you use

---

## 💰 Cost Models

### 🔹 CAPEX (Capital Expenditure)

* Up-front investment in hardware
* Physical data centers
* High maintenance cost
* Limited scalability

### 🔹 OPEX (Operational Expenditure)

* Pay-as-you-go
* No upfront hardware cost
* Scales on demand
* Managed by cloud provider

👉 **Cloud follows OPEX model**

---

## 🧾 Azure Account Sign-Up Requirements

To create an Azure account, you need:

* 💳 **Debit / Credit Card** (for identity verification)
* 📧 **Email Address**
* 📱 **Mobile Number**

🔗 Access Azure Portal:
👉 **[https://portal.azure.com](https://portal.azure.com)**

---

## 🌍 Cloud Concepts

### 🔹 Latency

* Time taken for data to travel from source to destination
* Lower latency = better performance
* Depends on region & network distance

### 🔹 Terms & Conditions

* Usage policies
* Data compliance
* Service limitations
* SLA (Service Level Agreement)

---

## ⚙️ Cloud Compute Pricing Models

### 🔹 On-Demand Instances

* Pay per second/minute
* No long-term commitment
* Suitable for production & critical workloads

### 🔹 Spot Instances

* Unused cloud capacity
* Up to 70–90% cheaper
* Can be terminated anytime
* Best for testing, batch jobs, non-critical workloads

---

## 🧰 Azure CLI (Command Line Interface)

**Azure CLI** is a cross-platform command-line tool used to manage Azure resources.

* Works on **Linux, macOS, Windows**
* Uses `az` commands
* Ideal for automation & scripting

Example:

```bash
az login
az account list
az group create
```

---

## 🖥️ Shells (Command Interpreters)

### 🔹 Common Shells

* **bash** – Bourne Again Shell
* **powershell** – Windows & cross-platform
* **dash** – Lightweight shell
* **ksh** – Korn shell
* **zsh** – Z shell (popular on macOS)

---

## 📦 Package Managers

Package managers install, update, and manage software.

### 🔹 Linux

* **Ubuntu / Debian** → `apt`
* **RedHat / CentOS / Rocky** → `yum`, `dnf`

### 🔹 macOS

* **Homebrew** → `brew update`

### 🔹 Windows

* **winget**
* **chocolatey (choco)**

---

## 🧾 Azure Subscription Types

### 🔹 Pay-As-You-Go

* Pay only for usage
* No commitment

### 🔹 Free Trial

* 1-month free
* Free credits
* Limited services

### 🔹 Enterprise

* Large organizations
* Custom billing
* Advanced support plans

---

## 🏢 Azure Organizational Hierarchy

```
Tenant (Microsoft Entra ID)
   |
Management Groups
   |
Subscriptions
   |
Resource Groups
   |
Resources
```

---

## 🔐 Tenant (Microsoft Entra ID)

* Acts as **root identity**
* Manages users, groups, roles
* One tenant can have multiple subscriptions

---

## 🧭 Management Groups

* Used for **governance**
* Apply policies across multiple subscriptions
* Enforce compliance & security

---

## 💳 Subscriptions

* Billing boundary
* Controls cost & quotas
* Linked to one tenant

---

## 📁 Resource Group (RG)

* Logical container for resources
* Resources share lifecycle
* Delete RG → deletes all resources inside

---

## 🧱 Resources

* Actual workloads
* Examples:

  * Virtual Machines
  * Storage Accounts
  * Databases
  * Load Balancers
  * VNets

---

## 🏷️ Tags

* Key-value pairs
* Used for:

  * Cost tracking
  * Ownership
  * Environment (dev/test/prod)

Example:

```
Environment = Production
Owner = DevOpsTeam
```

---

## 🔑 IAM (Identity & Access Management)

Controls **who can access what** in Azure.

### 🔹 Common Roles

* **Global Admin** – Full tenant access
* **Departmental Admin** – Limited scope access
* **Billing Admin** – Manages billing & invoices

👉 Uses **Role-Based Access Control (RBAC)**

---

## 🎯 Key Points to Remember (Exam / Interview)

* Cloud = OPEX model
* Azure Portal = portal.azure.com
* Tenant = Microsoft Entra ID
* Resource Group = logical boundary
* Subscription = billing boundary
* IAM = access control
* Spot instances = cheap but interruptible

---
