
````markdown
# 🚀 Google Cloud Functions - UI Deployment Guide

A step-by-step guide to creating, deploying, and testing a basic **HTTP-triggered** Cloud Function using the **Google Cloud Console UI**.

---

## 🧱 Step 1: Open Google Cloud Console
- Visit: [https://console.cloud.google.com/functions](https://console.cloud.google.com/functions)
- Select your GCP project or create a new one.

---

## ⚙️ Step 2: Enable Required APIs
Ensure the following APIs are **enabled**:
- ✅ Cloud Functions API  
- ✅ Cloud Build API  
- ✅ Artifact Registry API (optional but recommended for Node.js >18, or private deployments)

---

## ➕ Step 3: Click **Create Function**
- Click the **"CREATE FUNCTION"** button in the Functions dashboard.

---

## 📄 Step 4: Basic Configuration
| Field | Value |
|-------|-------|
| **Function name** | `helloWorld` |
| **Region** | `us-central1` |
| **Environment** | `1st generation` |
| **Trigger type** | `HTTP` |
| **Authentication** | `Allow unauthenticated` (✅ if public access is needed)

---

## 🔧 Step 5: Runtime Configuration
| Field | Value |
|-------|-------|
| **Runtime** | Node.js 20 |
| **Entry point** | `helloWorld` |

---

## 💻 Step 6: Write Your Code

### `index.js`:
```js
exports.helloWorld = (req, res) => {
  const name = req.query.name || 'World';
  res.send(`Hello, ${name}!`);
};
````

### `package.json`:

```json
{
  "name": "hello-world",
  "version": "1.0.0",
  "main": "index.js",
  "dependencies": {}
}
```

> ✅ You can also use **inline editor**, upload a `.zip` file, or choose from a **source repository (Cloud Source Repositories or GitHub)**.

---

## 🚀 Step 7: Deploy the Function

* Click **Deploy**
* Wait for a few moments until deployment finishes.

---

## 🌐 Step 8: Invoke the Function

### 📍 How to Test:

1. Click on the deployed function name.
2. Go to the **Trigger tab**
3. Copy the provided HTTPS URL (e.g., `https://<REGION>-<PROJECT_ID>.cloudfunctions.net/helloWorld`)
4. Append a query string to test:

```bash
https://.../helloWorld?name=Surendra
```

---

## 📄 Step 9: Monitor Logs

* Go to the **Logs tab** to:

  * View function execution results
  * Debug errors and inspect output
* Or use CLI:

```bash
gcloud functions logs read helloWorld
```

---

## 🛡️ Security Considerations

* ✅ If sensitive, **disallow unauthenticated access**
* Use IAM roles to restrict invocation (e.g., `Cloud Functions Invoker`)
* Use **Environment Variables** for secrets or configs (available in advanced settings)

---

## 💰 Pricing Notes

* Cloud Functions follow **pay-as-you-go pricing** based on:

  * **Invocations**
  * **Compute time**
  * **Outbound data**

Free tier includes:

* 2 million invocations/month
* 400,000 GB-seconds and 200,000 CPU-seconds

---

## 💡 Optional Enhancements

* 🔁 Use **Environment Variables** (in Runtime, build, and connections settings)
* 🌍 Use **2nd gen environment** for better concurrency and resource limits
* 🔄 Automate via `gcloud` CLI or CI/CD with GitHub Actions

---

## ✅ Summary

| Task              | Status |
| ----------------- | ------ |
| Project Selected  | ✅      |
| APIs Enabled      | ✅      |
| Code Written      | ✅      |
| Function Deployed | ✅      |
| URL Tested        | ✅      |
| Logs Verified     | ✅      |

---
