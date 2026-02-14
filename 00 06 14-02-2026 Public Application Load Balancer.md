# 🌐 Public Application Load Balancer – Azure Lab Documentation

This lab demonstrates how to deploy two Ubuntu web servers in a Virtual Network and distribute traffic using an **Azure Public Application Load Balancer**.

---

## 🏗️ Architecture Overview

![Image](https://sparxsystems.com/resources/gallery/diagrams/images/azure-example.png)

![Image](https://learn.microsoft.com/en-us/azure/load-balancer/media/quickstart-load-balancer-standard-internal-portal/internal-load-balancer-resources.png)

![Image](https://learn.microsoft.com/en-us/azure/load-balancer/media/quickstart-load-balancer-standard-public-portal/public-load-balancer-overview.png)

![Image](https://learn.microsoft.com/en-us/azure/load-balancer/media/load-balancer-components/outbound-rules.png)

**Components:**

* 1 Virtual Network (VNet)
* 1 Subnet
* 2 Virtual Machines (VM-A & VM-B)
* 1 Public Load Balancer
* Apache Web Server on both VMs

---

# 🧱 Step 1: Create Virtual Network

Create a VNet:

* **Name:** `myvnet`
* **Address Space:** `10.0.0.0/16`

Create Subnet:

* **Name:** `subnetA`
* **Subnet Range:** `10.0.1.0/24`

---

# 💻 Step 2: Create Virtual Machines

Create two Ubuntu VMs inside:

* **VNet:** `myvnet`
* **Subnet:** `subnetA`

VM Names:

* `vmA`
* `vmB`

Ensure:

* Public IP assigned (for initial testing)
* NSG allows inbound HTTP (Port 80)

---

# 🌐 Step 3: Install Apache Web Server (Run on Both VMs)

SSH into each VM and execute:

```bash
sudo apt update -y
sudo apt install apache2 -y
apache2 --version

sudo systemctl start apache2
sudo systemctl status apache2   # press q to exit
sudo systemctl enable apache2

cd /var/www/html
sudo chmod 755 /var/www/html
sudo rm index.html
sudo touch index.html
ls
sudo nano index.html
```

Inside `index.html`:

For **VM-A**

```html
<h1> Webserver 1 </h1>
```

For **VM-B**

```html
<h1> Webserver 2 </h1>
```

---

# 🔎 Step 4: Verify Individual VM Access

Access via Public IP:

```
http://20.102.96.140/
http://20.127.163.166/
```

You should see different web pages:

* Webserver 1
* Webserver 2

---

# ⚖️ Step 5: Create Public Load Balancer

In Azure Portal:

Create → Load Balancer

* **Type:** Public
* **SKU:** Standard
* **Region:** Same as VMs

---

# 🌍 Step 6: Create Frontend IP

* Create new Public IP
* Associate it with Load Balancer frontend

Example:

```
http://20.62.231.159/
```

---

# 🔁 Step 7: Create Backend Pool

* Go to Backend Pools
* Add Backend Pool
* Select:

  * **Virtual Network:** `myvnet`
  * Add:

    * `vmA`
    * `vmB`

---

# ❤️ Step 8: Create Health Probe

* Protocol: HTTP
* Port: 80
* Path: /

---

# 🔄 Step 9: Create Load Balancing Rule

* Frontend Port: 80
* Backend Port: 80
* Protocol: TCP
* Associate:

  * Frontend IP
  * Backend Pool
  * Health Probe

Click **Create**

---

# ✅ Step 10: Test Load Balancer

Open:

```
http://20.62.231.159/
```

Refresh multiple times.

You will observe traffic distribution between:

* Webserver 1
* Webserver 2

This confirms **Load Balancer distributing traffic across backend pool VMs.**

---

# 📌 Final Result

✔ Public Application Load Balancer created
✔ Two backend VMs configured
✔ Apache running on both
✔ Traffic distributed across servers

---
