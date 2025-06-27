
````markdown
# 🔐 GCP IAM Lab - Step-by-Step Guide

Learn how to manage Identity and Access Management (IAM) in Google Cloud by creating users, assigning roles, creating service accounts, and validating permissions.

---

## 📁 Step 1: Create a New GCP Project

1. Go to [https://console.cloud.google.com](https://console.cloud.google.com)
2. Click the **project dropdown** in the top navigation bar
3. Click **New Project**
4. **Project Name**: `iam-lab-project`
5. Click **Create**

---

## 👥 Step 2: Add a New IAM User

1. Navigate to **IAM & Admin > IAM**
2. Click **Grant Access**
3. Enter a Google email (e.g., another Gmail account)
4. Select **Role**: `Project > Viewer`
5. Click **Save**

🔸 _This grants read-only access to all project resources._

---

## ➕ Step 3: Add Another Role to the User

1. Click **Edit** next to the user’s name in the IAM list
2. Click **+ Add Another Role**
3. Select **Role**: `Storage > Storage Admin`
4. Click **Save**

🔸 _User now has read-only access to the project + full control over Cloud Storage._

---

## 🤖 Step 4: Create a Service Account

1. Navigate to **IAM & Admin > Service Accounts**
2. Click **Create Service Account**
   - Name: `demo-service-account`
   - ID: (auto-generated)
3. Assign **Role**: `Compute Engine > Compute Admin`
4. Click **Done**

🔸 _This service account can manage Compute Engine instances._

---

## 🖥️ Step 5: Create a VM and Assign Service Account

1. Navigate to **Compute Engine > VM Instances**
2. Click **Create Instance**
3. Configure:
   - **Name**: `test-vm`
   - **Region/Zone**: `us-central1-a` (or your preferred zone)
4. Under **Identity and API Access**:
   - **Service account**: Select `demo-service-account`
   - **Access Scopes**: Select "Allow full access" (or customize)
5. Click **Create**

---

## 🧪 Step 6: Test Permissions

1. **SSH** into the `test-vm`
2. Run the following commands to test service account permissions:

```bash
# List all Compute instances in the project
gcloud compute instances list

# Try accessing Cloud Storage if permissions are available
gsutil ls
````

✅ If the service account has appropriate roles, these commands will succeed.

---

## ⚠️ Bonus: Revoke Role and Observe Access Failure

1. Go to **IAM**
2. Find the user with `Storage Admin` role
3. Click **Edit > Delete Role**
4. Click **Save**
5. Ask the user to try creating or deleting a Cloud Storage bucket
6. They should now get a **Permission Denied** error

---

## 🛡️ Roles Used in This Lab

| Role                    | Purpose                                   |
| ----------------------- | ----------------------------------------- |
| Project > Viewer        | Read-only access to all resources         |
| Storage > Storage Admin | Full control over Cloud Storage           |
| Compute > Compute Admin | Manage VM instances and related resources |

---

## 🔍 Additional Tips

* Use **IAM Policy Troubleshooter**:
  IAM > Policy Troubleshooter to verify if a user has access to a specific resource

* Use **Service Account Keys** *(for local testing — not recommended for prod)*:

  * IAM > Service Accounts > `demo-service-account` > Keys > Add Key > JSON

* You can also use `gcloud` CLI for all IAM operations:

```bash
gcloud projects add-iam-policy-binding iam-lab-project \
  --member="user:someone@gmail.com" \
  --role="roles/storage.admin"
```

---

✅ Save this file as `gcp-iam-lab-guide.md` for versioning and tracking in your GitHub repo.

```

---

```
