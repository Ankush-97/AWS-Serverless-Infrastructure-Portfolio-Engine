# 🚀 Production-Grade AWS Serverless Portfolio Infrastructure (`ankush.fun`)

A high-performance, enterprise-grade personal portfolio platform engineered on a 100% Serverless AWS Infrastructure. The frontend application utilizes globally distributed delivery node layers to secure and fetch multi-layered web files asynchronously, eliminating server overhead costs. The contact subsystem leverages dynamic serverless event ingestion routes to process spam-protected contact ingest vectors securely into verified administrator streams.

---

## 🏗️ Architectural Infrastructure Workflow Design

This architecture diagram illustrates the end-to-end data pipeline traffic routing matrix across the application platform, handling standard user sessions and asynchronous contact ingest vectors securely:

```text
[ USER BROWSER CLIENT ]
          │
    (DNS Lookup for ankush.fun)
          ▼
   [ AWS Route 53 ] 
    (Authoritative Nameservers)
          │
    (Points to CloudFront Distribution)
          ▼
[ AWS CloudFront Edge Network ] (HTTPS / SSL/TLS Termination)
          │
          ├─► [ AWS S3 Bucket ] (Static Web Layer: HTML, CSS, JS)
          │
    (User Form Submit Request)
          ▼
[ Amazon API Gateway HTTP API ] (CORS Handshake Protected Layer)
          │
     (Method Route: POST /contact)
          ▼
[ AWS Lambda Endpoint ] 
  - Runtime: Python 3.x
  - Single Execution Constraint
  - Fault-Tolerant Retry Guard = 0 (Asynchronous Loop Protection)
          │
     (Filtered Payload)
          ▼
[ Amazon SES Component ] 
  - Region: ap-south-1 (Mumbai)
  - Sender Identity Verification Enforced
          │
     (Secure Transport Layer Email Delivery)
          ▼
[ VERIFIED TARGET ADMIN INBOX 📬 ]
```

---

## 🛠️ Technical Implementation Architecture Matrix

### 1. Authoritative DNS & Secure Edge Layer (AWS Route 53 & CloudFront)
* **Domain Registry Routing:** Transferred active namespace authorization controllers for `ankush.fun` from external registrars over onto an **AWS Route 53 Hosted Zone**.
* **Global Content Delivery Network:** Mapped root web queries to **AWS CloudFront Edge Locations** to ensure globally minimized latency via asset caching mechanisms.
* **SSL/TLS Automated Encryption:** Configured an **AWS Certificate Manager (ACM)** public certificate to enforce automated wildcard-ready HTTPS connection profiles globally, establishing hard encryption standards and a `Redirect HTTP to HTTPS` viewer protocol routing matrix.

### 2. Static Asset Storage Layer (AWS S3)
* **High-Availability Web Hosting:** Deployed core application static modules (`index.html`, style arrays, and scripts) directly into a decoupled object storage system optimized for zero-compute static endpoint evaluation.
* **Access Boundary Protection:** Hard-coded specific Bucket Resource Policies restricted explicitly to granular read operations (`s3:GetObject`), eliminating surface exposures to administrative data buckets.

### 3. Serverless Event Ingestion Backend (AWS Lambda & API Gateway)
* **Decoupled API Endpoint Vector:** Form actions route asynchronously through an **Amazon API Gateway HTTP API** layer, executing strict cross-origin preflight handshakes (CORS) bound to explicit routing targets.
* **Serverless Compute Logics:** The backend logic operates isolated within an **AWS Lambda function** environment leveraging Python. Compute lifecycle resources activate on-demand, terminating costs during application idle periods.
* **Data Sanitization Enforcements:** Custom structural processing filters reject empty variants, missing schemas, or corrupt payload definitions before authorizing target operations.

### 4. Downstream Mail Delivery Processing (AWS SES)
* **Identity Ingestion Pipeline:** Outbound notifications process securely through highly restricted **Amazon SES** sandboxed pipelines bound to explicitly verified target email communication systems.
* **Delivery Framework:** Automatically compiles sanitized data feeds incoming from the backend computational layers and processes downstream outbound delivery calls over secure transport layers.

---

## 🔄 Automated CI/CD Lifecycle Pipeline (GitHub Actions)

The platform repository features an autonomous infrastructure sync workflow that updates web views immediately without manual intervention:

1. **Trigger Condition:** Pushes or merged branches targeting the codebase core branch immediately awaken the automated runner frameworks.
2. **Secure Key Exchange:** Temporary runner containers connect securely using abstracted environment secrets containing highly restrictive deployment access signatures.
3. **Differential File Syncing:** Automation commands evaluate active asset differences and run an administrative synchronization routine to update modified components on the live application layer instantly.
