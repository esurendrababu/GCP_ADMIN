
---

# ☁️ GCP vs AWS Cheat Sheet

> A side-by-side comparison of key services between Google Cloud Platform (GCP) and Amazon Web Services (AWS) with practical notes and insights.

---

## 🚀 Compute

| Feature               | AWS               | GCP                            | Notes                              |
| --------------------- | ----------------- | ------------------------------ | ---------------------------------- |
| Virtual Machines      | EC2               | Compute Engine                 | GCP offers custom machine types    |
| Serverless Functions  | Lambda            | Cloud Functions                | Pay per execution                  |
| Containers            | ECS / Fargate     | Cloud Run                      | Fully managed container execution  |
| Kubernetes            | EKS               | GKE (Google Kubernetes Engine) | GKE is considered more mature      |
| Platform-as-a-Service | Elastic Beanstalk | App Engine                     | Deploy code without managing infra |

---

## 📦 Storage

| Feature          | AWS     | GCP              | Notes                                     |
| ---------------- | ------- | ---------------- | ----------------------------------------- |
| Object Storage   | S3      | Cloud Storage    | Both support Standard, Nearline, Coldline |
| Block Storage    | EBS     | Persistent Disks | Attached to VMs                           |
| File Storage     | EFS     | Filestore        | Network-attached storage                  |
| Archival Storage | Glacier | Archive Storage  | Long-term data retention                  |

---

## 🗃️ Databases

| Feature        | AWS         | GCP           | Notes                                    |
| -------------- | ----------- | ------------- | ---------------------------------------- |
| Managed SQL    | RDS         | Cloud SQL     | Supports MySQL, PostgreSQL, SQL Server   |
| Scalable SQL   | Aurora      | Cloud Spanner | Globally distributed, horizontal scaling |
| NoSQL          | DynamoDB    | Firestore     | Serverless, low-latency key-value store  |
| Data Warehouse | Redshift    | BigQuery      | Serverless and scalable analytics        |
| In-Memory DB   | ElastiCache | Memorystore   | Redis / Memcached support                |

---

## 🌐 Networking

| Feature         | AWS             | GCP                  | Notes                                   |
| --------------- | --------------- | -------------------- | --------------------------------------- |
| Virtual Network | VPC             | VPC                  | GCP VPC is global; AWS is regional      |
| Load Balancing  | ELB / ALB / NLB | Cloud Load Balancing | GCP offers global HTTP(S) LB            |
| NAT Gateway     | NAT Gateway     | Cloud NAT            | Outbound internet for private instances |
| CDN             | CloudFront      | Cloud CDN            | Fast content delivery                   |
| DNS             | Route 53        | Cloud DNS            | Global DNS management                   |

---

## 🔒 Security & Identity

| Feature           | AWS                    | GCP            | Notes                       |
| ----------------- | ---------------------- | -------------- | --------------------------- |
| Identity & Access | IAM                    | IAM            | Fine-grained RBAC           |
| Key Management    | KMS                    | Cloud KMS      | Encrypt secrets and data    |
| Secret Storage    | Secrets Manager        | Secret Manager | Secure secret handling      |
| Policy/Firewall   | Security Groups, NACLs | Firewall Rules | Control traffic to/from VMs |

---

## 📊 Monitoring & Logging

| Feature              | AWS             | GCP              | Notes                                |
| -------------------- | --------------- | ---------------- | ------------------------------------ |
| Metrics & Dashboards | CloudWatch      | Cloud Monitoring | Performance observability            |
| Logging              | CloudTrail      | Cloud Audit Logs | Track API usage and resource changes |
| Log Management       | CloudWatch Logs | Cloud Logging    | Query and analyze logs               |

---

## ⚙️ DevOps & CI/CD

| Feature          | AWS                     | GCP                           | Notes                           |
| ---------------- | ----------------------- | ----------------------------- | ------------------------------- |
| CI/CD Tools      | CodeBuild, CodePipeline | Cloud Build, Cloud Deploy     | End-to-end automation           |
| Git Repositories | CodeCommit              | Cloud Source Repositories     | Hosted Git repos                |
| IaC Support      | CloudFormation, CDK     | Deployment Manager, Terraform | GCP supports Terraform natively |

---

## 🧠 AI/ML & Big Data

| Feature            | AWS                     | GCP            | Notes                           |
| ------------------ | ----------------------- | -------------- | ------------------------------- |
| Machine Learning   | SageMaker               | Vertex AI      | Full ML lifecycle platforms     |
| Data Lakes         | Lake Formation          | BigLake        | Unified data lakes              |
| Data Pipelines     | AWS Glue, Data Pipeline | Cloud Dataflow | ETL and stream/batch processing |
| Messaging / Queues | SQS, SNS                | Pub/Sub        | Asynchronous messaging          |

---

## 🧰 Developer Tools & CLI

| Feature     | AWS        | GCP                    | Notes                             |
| ----------- | ---------- | ---------------------- | --------------------------------- |
| CLI Tool    | AWS CLI    | gcloud CLI             | GCP uses `gcloud`, AWS uses `aws` |
| SDK         | AWS SDK    | Cloud Client Libraries | Available for multiple languages  |
| Cloud Shell | CloudShell | CloudShell             | Web-based terminal                |

---

