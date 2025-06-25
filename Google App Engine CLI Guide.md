
---

# ☁️ Google App Engine CLI Guide

---

## 📁 App Engine Initialization

```bash
gcloud app create
```

Initializes App Engine for your project. You’ll be prompted to choose a region.

---

## 🚀 Deploy Application

```bash
gcloud app deploy
gcloud app deploy app.yaml
gcloud app deploy app.yaml --version=[VERSION_ID]
```

Deploys your app to App Engine.

---

## 🌍 View Deployed Services

```bash
gcloud app browse
gcloud app services list
```

Opens the app in a browser or lists deployed services.

---

## 🔄 Manage Versions

```bash
gcloud app versions list
gcloud app versions delete [VERSION_ID]
gcloud app versions migrate [VERSION_ID]
```

Used to manage different versions of your app.

---

## 🔁 Scaling & Traffic Splitting

```bash
gcloud app services set-traffic SERVICE --splits VERSION=TRAFFIC
```

**Example:**

```bash
gcloud app services set-traffic default --splits v1=0.5,v2=0.5
```

This splits traffic between different versions of your app.

---

## 🛑 Stop & Start Versions

```bash
gcloud app versions stop [VERSION_ID]
gcloud app versions start [VERSION_ID]
```

---

## 🧾 Logs

```bash
gcloud app logs tail
gcloud app logs read
```

View or stream logs for your App Engine app.

---

## 🔐 Firewall Rules

```bash
gcloud app firewall-rules list
gcloud app firewall-rules create [PRIORITY] --action=ALLOW|DENY --source-range=IP_RANGE
```

---

## ⚙️ Configuration

```bash
gcloud app describe
gcloud app regions list
```

Describe your App Engine setup or view available regions.

---

