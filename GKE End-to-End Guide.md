
````markdown
# ☸️ Google Kubernetes Engine (GKE) - End-to-End Guide

Google Kubernetes Engine (GKE) is a fully managed Kubernetes service by Google Cloud, used to deploy, manage, and scale containerized applications effortlessly.

---

## 🧩 1. What is GKE?

**Google Kubernetes Engine (GKE)** is a managed service that simplifies the deployment, management, and scaling of Kubernetes clusters in the cloud.

---

## 🚀 2. Enable GKE API

### Via Console:
- Go to **APIs & Services > Library**
- Enable **Kubernetes Engine API**

---

## ⚙️ 3. Create a GKE Cluster

### ✅ Using Console:
- Navigate to **Kubernetes Engine > Clusters**
- Click **Create Cluster**
- Choose **Standard** or **Autopilot**
- Configure number of nodes, machine type, etc.

### ✅ Using CLI:
```bash
gcloud container clusters create my-cluster \
  --num-nodes=3 \
  --zone=us-central1-a
````

---

## 🔧 4. Install and Configure kubectl

```bash
gcloud components install kubectl
gcloud container clusters get-credentials my-cluster \
  --zone=us-central1-a
```

---

## 🐳 5. Deploy a Simple Application

Create a file called `deployment.yaml`:

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
      - name: my-app
        image: gcr.io/google-samples/hello-app:1.0
        ports:
        - containerPort: 8080
```

Deploy it using:

```bash
kubectl apply -f deployment.yaml
```

---

## 🌐 6. Expose Your Application

```bash
kubectl expose deployment my-app \
  --type=LoadBalancer \
  --port=80 \
  --target-port=8080
```

---

## 📈 7. Scale the Application

```bash
kubectl scale deployment my-app --replicas=5
```

---

## 🔍 8. Monitor Pods & View Logs

```bash
kubectl get pods
kubectl logs <pod-name>
```

---

## 🔄 9. Update the Application

```bash
kubectl set image deployment/my-app my-app=gcr.io/google-samples/hello-app:2.0
```

---

## 🧹 10. Delete the GKE Cluster

```bash
gcloud container clusters delete my-cluster --zone=us-central1-a
```

---

## 💡 Example Use Case: Frontend & Backend App

* Deploy **React frontend** & **Node.js / Flask backend**
* Use `ClusterIP` for backend service
* Use `LoadBalancer` for frontend service
* Frontend communicates with backend using **internal DNS**
* Monitor using:

  * `kubectl get pods`
  * `kubectl logs <pod-name>`
  * `kubectl top pods` (requires metrics server)
  * **Cloud Monitoring**
  * Optionally use **Prometheus + Grafana** for detailed insights

---

```
