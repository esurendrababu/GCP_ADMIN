
---

# 🧪 Lab Guide: Deploying Frontend & Backend Apps on GCP Using Managed Instance Groups (MIGs) and HTTP Load Balancer

---

## 📅 Objective

Deploy a basic **frontend** and **backend** application using **Managed Instance Groups (MIGs)** and a **HTTP Load Balancer** to demonstrate traffic distribution across instances.

---

## 🛠️ Prerequisites

* A GCP Project with billing enabled
* Compute Engine, Cloud Load Balancing, and Monitoring APIs enabled
* IAM roles: Compute Admin, Load Balancer Admin (or Owner)

---

## 🔹 Step 1: Create Instance Templates

### ◾ Frontend Template

```bash
#! /bin/bash
apt update -y
apt install apache2 -y
echo "<h1>Frontend $(hostname)</h1>" > /var/www/html/index.html
systemctl restart apache2
```

### ◾ Backend Template

```bash
#! /bin/bash
apt update -y
apt install apache2 -y
echo "<h1>Backend $(hostname)</h1>" > /var/www/html/index.html
systemctl restart apache2
```

---

## 🔹 Step 2: Create Managed Instance Groups (MIGs)

Create `frontend-mig` and `backend-mig` in `us-central1-a`, each with 2 instances using their respective templates.

---

## 🔹 Step 3: Create Health Check

* Name: `http-health-check`
* Protocol: HTTP
* Port: 80
* Path: `/`

---

## 🔹 Step 4: Create Load Balancer

* Type: `HTTP(S)`
* Backend: `frontend-mig`
* Health Check: `http-health-check`
* Path Rules: default → frontend
* Frontend: Ephemeral IP, Port 80

---

## 🔹 Step 5: Test the Load Balancer

Visit the external IP of the Load Balancer. Refresh to see hostname variation from frontend instances.

---

## 🚀 Optional: API Routing

Route `/api/*` to a backend service connected to `backend-mig`.

---

## 🔹 gcloud CLI Automation

```bash
gcloud compute instance-groups managed create frontend-mig \
  --template=frontend-template --size=2 --zone=us-central1-a

gcloud compute instance-groups managed create backend-mig \
  --template=backend-template --size=2 --zone=us-central1-a
```

---

## 🌐 Outcome

A scalable, load-balanced frontend and backend architecture on GCP using MIGs and Load Balancer.

---
