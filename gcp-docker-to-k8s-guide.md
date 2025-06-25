# 🚀 Docker to Kubernetes Guide (GCP Edition)

---

## 1️⃣ Docker Setup

### 🐳 Install Docker

```bash
curl -fsSL https://get.docker.com | bash
sudo systemctl start docker
sudo systemctl enable docker
```

### ✅ Verify Installation

```bash
docker --version
docker ps
```

---

## 2️⃣ Build and Push Docker Image

### ✨ Create a Sample Web App

**index.html**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Docker App</title>
</head>
<body>
    <h1>Welcome to Dockerized App!</h1>
</body>
</html>
```

### 🛠 Dockerfile to Build the Image

```Dockerfile
FROM nginx:latest
COPY index.html /usr/share/nginx/html/
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

### 🔧 Build and Run Docker Image

```bash
docker build -t my-nginx-image .
docker run -d -p 8080:80 my-nginx-image
```

### ☁️ Push Docker Image to GCR

```bash
docker tag my-nginx-image gcr.io/<PROJECT-ID>/my-nginx-image
gcloud auth configure-docker
docker push gcr.io/<PROJECT-ID>/my-nginx-image
```

---

## 3️⃣ Deploy to Kubernetes

### ⚙️ Set Up Kubernetes Cluster

**Option 1: Local Cluster (Minikube)**

```bash
minikube start
kubectl get nodes
```

**Option 2: Multi-Node Cluster with kubeadm**

```bash
sudo kubeadm init --pod-network-cidr=192.168.1.0/16
kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml
```

### 📄 Create a Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-nginx-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-nginx-app
  template:
    metadata:
      labels:
        app: my-nginx-app
    spec:
      containers:
      - name: my-nginx-app
        image: gcr.io/<PROJECT-ID>/my-nginx-image
        ports:
        - containerPort: 80
```

### 🚀 Apply Deployment

```bash
kubectl apply -f deployment.yaml
```

### 🌐 Expose as a Service

```bash
kubectl expose deployment my-nginx-app --type=LoadBalancer --port=80
```

---

## 4️⃣ Manage Kubernetes Cluster

### 📋 Check Status

```bash
kubectl get pods
kubectl get deployments
kubectl get services
```

### 🧾 Logs and Debugging

```bash
kubectl logs <POD-NAME>
kubectl describe pod <POD-NAME>
```

### 🔄 Scale Deployment

```bash
kubectl scale deployment my-nginx-app --replicas=5
```

### ❌ Delete Resources

```bash
kubectl delete deployment my-nginx-app
kubectl delete service my-nginx-app
```

---

## 5️⃣ Monitor Kubernetes Cluster

### 📊 Cluster Info

```bash
kubectl cluster-info
kubectl get nodes
kubectl top pods
kubectl top nodes
```

---

## 🎯 Next Steps

✅ Set up Helm for package management  
✅ Configure Ingress for advanced routing  
✅ Implement CI/CD pipelines with GitHub Actions
