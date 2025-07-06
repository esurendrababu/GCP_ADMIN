# ☁️ Google Cloud Functions - UI Deployment Guide

---

## 📘 What is Google Cloud Function?

**Cloud Functions** is a lightweight, serverless compute service offered by GCP. It lets you run backend code in response to events (like HTTP requests, Cloud Pub/Sub messages, or Cloud Storage triggers) **without managing servers**.

### ✅ Key Features:
- Event-driven & auto-scalable
- Billed per 100ms of execution time
- Supports multiple runtimes (Node.js, Python, Go, Java, etc.)
- Integrates with other GCP services

---

## 💡 Common Use Cases:
- Handling HTTP requests (REST APIs)
- Responding to file uploads in Cloud Storage
- Processing Pub/Sub messages
- Running lightweight backend logic
- Automating tasks via event triggers
- Sending notifications or emails

---

## 🧪 Step-by-Step UI Deployment Guide

---

### 🪟 Step 1: Open Google Cloud Console
- Navigate to: [https://console.cloud.google.com/functions](https://console.cloud.google.com/functions)
- Ensure you're in the correct **GCP Project**.

---

### 🛠️ Step 2: Enable Required APIs
When prompted, enable the following APIs:
- ✅ Cloud Functions API  
- ✅ Cloud Build API  
- 🔁 (Optional but recommended): Artifact Registry API

---

### ➕ Step 3: Click 'Create Function'
- Click on the **"CREATE FUNCTION"** button to start deployment.

---

### ⚙️ Step 4: Basic Settings

| Setting              | Value             |
|----------------------|-------------------|
| Function name        | `helloWorld`      |
| Region               | `us-central1`     |
| Environment          | `1st Generation`  |
| Trigger Type         | `HTTP`            |
| Authentication       | Allow unauthenticated |

---

### 🔧 Step 5: Runtime Settings

| Setting              | Value         |
|----------------------|---------------|
| Runtime              | Node.js 20    |
| Entry point function | `helloWorld`  |

---

### 🧠 Step 6: Write Your Function Code

#### `index.js`
```javascript
exports.helloWorld = (req, res) => {
  const name = req.query.name || 'World';
  res.send(`Hello, ${name}!`);
};


**🚀 Step 7: Deploy the Function
**Click Deploy.

Wait for the process to complete.

🌍 Step 8: Invoke Your Function
Click on your deployed function.

Go to the Trigger tab.

Copy the auto-generated URL.

Open it in a browser with a query parameter like this:

url
Copy
Edit
https://REGION-PROJECT_ID.cloudfunctions.net/helloWorld?name=Surendra
📊 Monitor Logs & Output
Navigate to the Logs tab of the function

View real-time output, success messages, or errors

🔍 Or via CLI:
bash
Copy
Edit
gcloud functions logs read helloWorld
🔐 Security Considerations
✅ Choose “Allow unauthenticated” only for public APIs

For internal APIs, restrict access using IAM roles

Role: Cloud Functions Invoker

Avoid hardcoding secrets; instead use:

Environment variables

Secret Manager

💰 Pricing Information
Free tier: 2 million invocations/month, 400,000 GB-seconds

Billed based on:

Number of invocations

Duration (per 100ms)

Outbound data

✅ Summary Checklist
Task	Status
Project Selected	✅
APIs Enabled	✅
Function Created	✅
Code Written	✅
Function Deployed	✅
Trigger URL Tested	✅
Logs Verified	✅

