# 📘 gcloud CLI Commands for Creating and Managing VMs in Google Cloud

## ✅ Create a New VM Instance

```bash
gcloud compute instances create my-ubuntu-vm \
  --zone=us-central1-a \
  --machine-type=e2-medium \
  --image-family=ubuntu-2204-lts \
  --image-project=ubuntu-os-cloud
```

---

## 🔁 Common & Useful VM Commands

### 🖥️ List all VM instances

```bash
gcloud compute instances list
```

### 🔍 Get details of a specific VM

```bash
gcloud compute instances describe my-ubuntu-vm \
  --zone=us-central1-a
```

### ▶️ Start a stopped VM

```bash
gcloud compute instances start my-ubuntu-vm \
  --zone=us-central1-a
```

### ⏹️ Stop a running VM

```bash
gcloud compute instances stop my-ubuntu-vm \
  --zone=us-central1-a
```

### 🗑️ Delete a VM

```bash
gcloud compute instances delete my-ubuntu-vm \
  --zone=us-central1-a
```

### 🔐 SSH into a VM

```bash
gcloud compute ssh my-ubuntu-vm \
  --zone=us-central1-a
```

### 📁 Copy files to the VM

```bash
gcloud compute scp ./localfile.txt my-ubuntu-vm:/home/username/ \
  --zone=us-central1-a
```

### 📁 Copy files from the VM

```bash
gcloud compute scp my-ubuntu-vm:/home/username/remote.txt ./ \
  --zone=us-central1-a
```


