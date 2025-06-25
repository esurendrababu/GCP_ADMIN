# 🐳 Docker to GCR Deployment & 🚀 Kubernetes Deployment Guide

## Docker: Create, Customize, and Push to Google Container Registry (GCR)

### 📦 Step-by-Step: Build and Push Docker Image to GCR

1. **Run an NGINX container locally**
```bash
docker run -p 8080:80 nginx:latest
```

2. **Check all running/stopped containers**
```bash
docker ps -a
```

3. **Run the image in background mode**
```bash
docker run -d -p 8080:80 nginx:latest
```

4. **Create a custom HTML page**
- Create `index.html` with some basic HTML content.

5. **Copy the file into the running container**
```bash
docker cp index.html <container-id>:/usr/share/nginx/html/
```

6. **Commit the container as a new image**
```bash
docker commit <container-id> cad/web:version1
```

7. **Tag the image for GCR**
```bash
docker tag cad/web:version1 us.gcr.io/youtube-demo-255723/cad-site:version1
```

8. **Push the Docker image to GCR**
```bash
docker push us.gcr.io/youtube-demo-255723/cad-site:version1
```

> 💡 **Tips**:
> - Make sure Docker is authenticated with GCR.
> - Use `gcloud auth configure-docker` for authentication.

---

# 🚀 Kubernetes Deployment Guide

A concise guide to deploying apps using Kubernetes YAML files, LoadBalancer or Ingress for external access, and setting up CI/CD pipelines.

## 1️⃣ Deploy Applications Using Kubernetes YAML

### 📄 Sample Deployment Manifest

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
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
        image: gcr.io/<PROJECT-ID>/my-app-image:latest
        ports:
        - containerPort: 80
```

### 🔧 Apply the Deployment

```bash
kubectl apply -f deployment.yaml
kubectl get pods
kubectl get deployments
```

---

## 2️⃣ Set Up LoadBalancer or Ingress

### 🔹 LoadBalancer Service Example

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-app-service
spec:
  type: LoadBalancer
  selector:
    app: my-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
```

Apply the service:
```bash
kubectl apply -f service.yaml
kubectl get services
```

### 🔹 Ingress Controller and Rule

1. **Install NGINX Ingress Controller**
```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
```

2. **Create Ingress Rule**
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-app-ingress
spec:
  rules:
  - host: myapp.example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: my-app-service
            port:
              number: 80
```

Apply and verify:
```bash
kubectl apply -f ingress.yaml
kubectl get ingress
```

---

## 3️⃣ Implement CI/CD with GitHub Actions

Automate builds and deployments using GitHub Actions.

### 🛠 Sample GitHub Actions Workflow

`.github/workflows/deploy.yml`:

```yaml
name: Deploy to Kubernetes
on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout Code
      uses: actions/checkout@v2

    - name: Login to GCR
      run: |
        echo "${{ secrets.GCP_SA_KEY }}" | docker login -u _json_key --password-stdin https://gcr.io

    - name: Build and Push Docker Image
      run: |
        docker build -t gcr.io/<PROJECT-ID>/my-app-image:latest .
        docker push gcr.io/<PROJECT-ID>/my-app-image:latest

    - name: Deploy to Kubernetes
      run: |
        kubectl apply -f k8s-deployment.yaml
```

---
