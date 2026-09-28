# ☁️ CloudVault - AWS Serverless File Storage Application

CloudVault is a full-stack, serverless cloud file management web application built on AWS. It allows users to list, search, upload, download, and delete files securely in an Amazon S3 bucket via pre-signed URLs without routing heavy binary data through API Gateway.

🌐 **Live Demo:** [http://cloudvault-proj-2026-22m9.s3-website.ap-south-1.amazonaws.com](http://cloudvault-proj-2026-22m9.s3-website.ap-south-1.amazonaws.com)

---

## 🏗️ System Architecture

```text
[ User Web Browser ]
       │
       ├─── (1) HTTP REST API Requests (GET/POST/DELETE)
       │    └────────► [ Amazon API Gateway v2 ]
       │                      │
       │                      ▼
       │              [ AWS Lambda (Python 3.x) ]
       │                      │
       │                      ├─── (2) Generates Presigned URLs (Boto3)
       │                      └─── (3) Lists/Deletes Objects
       │                      │
       │                      ▼
       │              [ Amazon S3 Bucket ]
       │                      ▲
       └─── (4) Direct S3 Upload/Download via Presigned URLs