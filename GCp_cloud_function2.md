# Google Cloud Functions - UI & CLI Deployment Guide

## 🚀 Step 1: Open Google Cloud Console

* Visit: [https://console.cloud.google.com/functions](https://console.cloud.google.com/functions)
* Select your GCP project

## 💻 Step 2: Enable Required APIs

* Cloud Functions API ✅
* Cloud Build API ✅
* (Optional) Artifact Registry API ✅

## 📃 Step 3: Create the Function (UI Based)

* Click **"CREATE FUNCTION"**

## 🌐 Step 4: Basic Settings

* **Function Name**: `helloWorld`
* **Region**: `us-central1`
* **Environment**: 1st Gen or 2nd Gen
* **Trigger Type**: HTTP
* **Authentication**: Allow unauthenticated (only if public API)

## ⚖️ Step 5: Runtime Settings

* **Runtime**: Node.js 20
* **Entry Point**: `helloWorld`

## 📚 Step 6: Code the Function

### index.js:

```javascript
exports.helloWorld = (req, res) => {
  const name = req.query.name || 'World';
  res.send(`Hello, ${name}!`);
};
```

### package.json:

```json
{
  "name": "hello-world",
  "version": "1.0.0",
  "main": "index.js",
  "dependencies": {}
}
```

## 🚀 Step 7: Deploy the Function (UI)

* Click **Deploy**
* Wait for the deployment to complete

## 🌍 Step 8: Invoke Your Function

1. Click on your deployed function
2. Go to the **Trigger** tab
3. Copy the auto-generated URL
4. Test in browser:

```bash
https://REGION-PROJECT_ID.cloudfunctions.net/helloWorld?name=Surendra
```

Or via CLI:

```bash
curl "https://REGION-PROJECT_ID.cloudfunctions.net/helloWorld?name=Surendra"
```

## 📊 Monitor Logs

* Use **Logs** tab in Cloud Console
* Or via CLI:

```bash
gcloud functions logs read helloWorld
```

---

# 🧪 2nd Gen & CLI Deployment Guide

## Step 1: Prepare Your Code

(Same as above index.js and package.json)

## Step 2: Enable APIs (CLI)

```bash
gcloud services enable cloudfunctions.googleapis.com
```

## Step 3: Deploy using CLI (1st Gen)

```bash
gcloud functions deploy helloWorld \
  --runtime=nodejs20 \
  --trigger-http \
  --allow-unauthenticated \
  --entry-point=helloWorld \
  --region=us-central1
```

## Step 4: Deploy using CLI (2nd Gen)

```bash
gcloud functions deploy helloWorld \
  --gen2 \
  --runtime=nodejs20 \
  --trigger-http \
  --allow-unauthenticated \
  --entry-point=helloWorld \
  --region=us-central1 \
  --source=.
```

## Step 5: View Deployed Function

```bash
gcloud functions describe helloWorld --region=us-central1
```

## Step 6: Test the Function

```bash
curl "$(gcloud functions describe helloWorld --region=us-central1 --format='value(serviceConfig.uri)')?name=Surendra"
```

## 🔐 Security Considerations

* Use `--allow-unauthenticated` for public APIs only
* Use IAM Role: `roles/cloudfunctions.invoker` for restricted access
* Use Secret Manager & environment variables for sensitive data

## 💰 Pricing Info

* **Free Tier**: 2M invocations/month, 400,000 GB-seconds
* Billed by:

  * # of invocations
  * Execution time (100ms increments)
  * Outbound data

## ✅ Summary Checklist

| Task                | Status |
| ------------------- | ------ |
| Project Selected    | ✅      |
| APIs Enabled        | ✅      |
| Function Code Ready | ✅      |
| Deployed via UI/CLI | ✅      |
| Trigger Tested      | ✅      |
| Logs Verified       | ✅      |
| Security Configured | ✅      |
| Cost Awareness Done | ✅      |

---

## ❓ What is a Cloud Function?

Google Cloud Functions is a serverless compute service that lets you run your code in response to events without managing servers.

### 🌀 Common Use Cases

* HTTP REST APIs
* Cloud Storage triggers (file uploads)
* Firestore/Realtime DB triggers
* CI/CD workflows
* Automation jobs

