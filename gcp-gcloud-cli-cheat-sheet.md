

````markdown
# 🧠 GCP CLI (gcloud) Cheat Sheet

A quick reference for commonly used `gcloud` commands across various GCP services.

---

## 🔐 Configuration & Authentication

```bash
gcloud init                                    # Initialize SDK and login
gcloud auth login                              # Authenticate user account
gcloud config set project [PROJECT_ID]         # Set default project
gcloud config set compute/region REGION        # Set default region
gcloud config set compute/zone ZONE            # Set default zone
gcloud config list                              # View current configuration
gcloud auth list                                # List active authenticated accounts
gcloud info                                     # Display SDK info and project settings
````

---

## 🖥️ Compute Engine

```bash
gcloud compute instances create my-vm \
  --zone=us-central1-a                          # Create a new VM

gcloud compute instances list                   # List all VM instances
gcloud compute ssh my-vm                        # SSH into a VM instance
gcloud compute instances delete my-vm \
  --zone=us-central1-a                          # Delete VM

gcloud compute images list                      # List available OS images
gcloud compute disks list                       # List disks
gcloud compute snapshots list                   # List snapshots
gcloud compute machine-types list --zones=us-central1-a   # List machine types
```

---

## ☁️ Cloud Storage (gsutil-style now with `gcloud storage`)

```bash
gcloud storage buckets create gs://my-bucket    # Create bucket
gcloud storage buckets list                     # List all buckets
gcloud storage buckets delete gs://my-bucket    # Delete bucket

gcloud storage cp file.txt gs://my-bucket/      # Upload file
gcloud storage cp gs://my-bucket/file.txt .     # Download file

gcloud storage ls                                # List files and folders
gcloud storage rm gs://my-bucket/file.txt        # Delete file
```

---

## 🔐 IAM & Access Management

```bash
gcloud projects get-iam-policy [PROJECT_ID]     # View IAM policy
gcloud projects add-iam-policy-binding [PROJECT_ID] \
  --member="user:email@example.com" \
  --role="roles/viewer"                         # Add user with a role

gcloud iam roles list                           # List all predefined roles
gcloud iam service-accounts list                # List service accounts
gcloud iam service-accounts create my-sa        # Create service account

gcloud iam service-accounts keys create key.json \
  --iam-account=my-sa@[PROJECT_ID].iam.gserviceaccount.com  # Create key file
```

---

## 🧱 APIs & Services

```bash
gcloud services list                            # List all enabled APIs
gcloud services enable compute.googleapis.com   # Enable an API
gcloud services disable compute.googleapis.com  # Disable an API
```

---

## 🔁 Kubernetes (GKE)

```bash
gcloud container clusters list                  # List GKE clusters
gcloud container clusters create my-cluster \
  --num-nodes=3 --zone=us-central1-a            # Create cluster

gcloud container clusters get-credentials my-cluster \
  --zone=us-central1-a                          # Get kubeconfig

gcloud container clusters delete my-cluster \
  --zone=us-central1-a                          # Delete cluster
```

---

## 📦 Cloud Functions (Serverless)

```bash
gcloud functions deploy helloWorld \
  --runtime=nodejs20 \
  --trigger-http --allow-unauthenticated        # Deploy HTTP trigger function

gcloud functions call helloWorld                # Call the function
gcloud functions delete helloWorld              # Delete the function
```

---

## 📊 Monitoring & Billing

```bash
gcloud billing accounts list                    # List billing accounts
gcloud billing projects link [PROJECT_ID] \
  --billing-account [ACCOUNT_ID]                # Link billing to project

gcloud logging logs list                        # List logs
gcloud logging read "resource.type=gce_instance" \
  --limit 5                                     # Read logs for GCE
```

---

## 🧩 Miscellaneous

```bash
gcloud components update                        # Update the gcloud SDK
gcloud components list                          # List installed components
gcloud help                                     # View help
gcloud cheat-sheet                              # Access gcloud built-in cheat sheet
```

---



