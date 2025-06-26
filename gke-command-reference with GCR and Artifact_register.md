

````markdown
# ☸️ Google Kubernetes Engine (GKE) - Command Reference & Workflow

A comprehensive guide with step-by-step instructions and commands for deploying applications to Google Kubernetes Engine.

---

## 📌 1. Set Project and Region

```bash
gcloud config set project YOUR_PROJECT_ID
gcloud config set compute/region us-central1
````

---

## ⚙️ 2. Create a GKE Cluster

```bash
gcloud container clusters create my-cluster \
  --num-nodes=3 \
  --region=us-central1
```

---

## 🔐 3. Authenticate kubectl with the Cluster

```bash
gcloud container clusters get-credentials my-cluster \
  --region=us-central1
```

---

## 📄 4. Write Deployment YAML (deployment.yaml)

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-container
        image: gcr.io/YOUR_PROJECT_ID/my-image
        ports:
        - containerPort: 8080
```

---

## 🚀 5. Deploy the Application

```bash
kubectl apply -f deployment.yaml
```

---

## 🌐 6. Expose the Application

```bash
kubectl expose deployment my-app \
  --type=LoadBalancer \
  --port=80 \
  --target-port=8080
```

---

## 🔍 7. Check the External IP (wait a few minutes)

```bash
kubectl get service
```

---

## 🛠️ Additional Useful kubectl Commands

### 🔎 Inspect Resources

```bash
kubectl get pods
kubectl get deployments
kubectl get services
kubectl get nodes
```

### 📄 Describe and Logs

```bash
kubectl describe pod <POD_NAME>
kubectl logs <POD_NAME>
```

### 🚫 Delete Resources

```bash
kubectl delete service my-app
kubectl delete deployment my-app
```

### 📊 Monitor Cluster

```bash
kubectl top pods
kubectl top nodes
```

---

## ✅ Notes

### 🔸 Push Docker Image to Google Container Registry (GCR)

```bash
# Authenticate Docker with GCR
gcloud auth configure-docker

# Tag the image
docker tag my-image gcr.io/YOUR_PROJECT_ID/my-image

# Push the image to GCR
docker push gcr.io/YOUR_PROJECT_ID/my-image
```

### 🔸 Push Docker Image to Artifact Registry

```bash
# Enable the Artifact Registry API
gcloud services enable artifactregistry.googleapis.com

# Create a repository (one-time setup)
gcloud artifacts repositories create my-repo \
  --repository-format=docker \
  --location=us-central1 \
  --description="Docker repo"

# Authenticate Docker with Artifact Registry
gcloud auth configure-docker us-central1-docker.pkg.dev

# Tag the image
docker tag my-image us-central1-docker.pkg.dev/YOUR_PROJECT_ID/my-repo/my-image

# Push the image
docker push us-central1-docker.pkg.dev/YOUR_PROJECT_ID/my-repo/my-image
```

* Use `kubectl get pods` to monitor application status.
* For debugging, use `kubectl logs <pod-name>`.
* Use `kubectl port-forward` for local access to pods if needed.

---


```
