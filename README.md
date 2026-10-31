# 🚀 Production-Grade AWS Serverless Portfolio Infrastructure (`ankush.fun`)

A high-performance, enterprise-grade personal portfolio platform engineered on a 100% Serverless AWS Infrastructure. The frontend application utilizes globally distributed delivery node layers to secure and fetch multi-layered web files asynchronously, eliminating server overhead costs. The contact subsystem leverages dynamic serverless event ingestion routes to process spam-protected contact ingest vectors securely into verified administrator streams.

---


## 🏗️ Project Architecture & Connection Diagram

```mermaid
graph TD
    %% Styling
    classDef aws style fill:#FF9900,stroke:#fff,stroke-width:2px,color:#fff;
    classDef github style fill:#24292e,stroke:#fff,stroke-width:2px,color:#fff;
    classDef client style fill:#1f77b4,stroke:#fff,stroke-width:2px,color:#fff;

    %% Client Layer
    User[👤 User Browser Client]:::client
    User -->|1. Opens https://ankush.fun| Route53

    %% DNS & CDN Layer
    subgraph AWS Global Edge Infrastructure
        Route53[🗺️ AWS Route 53 <br> DNS Namespace Controller]:::aws
        CloudFront[⚡ AWS CloudFront CDN <br> SSL/HTTPS Termination]:::aws
        ACM[🔑 AWS Certificate Manager <br> Free SSL Certificate]:::aws
        
        Route53 -->|Points Domain Alias to| CloudFront
        ACM -->|Provides HTTPS Lock to| CloudFront
    end
    CloudFront -->|2. Pulls Static Assets| S3

    %% Storage & Deployment Layer
    subgraph Frontend Hosting & Automation
        S3[📦 AWS S3 Bucket <br> ankush.fun Static Host]:::aws
        GitHub[🐙 GitHub Repository <br> Source Code]:::github
        Actions[⚙️ GitHub Actions <br> CI/CD Runner Pipeline]:::github
        
        GitHub -->|Trigger: git push| Actions
        Actions -->|3. Auto Syncs Code via IAM| S3
    end

    %% Backend Form Ingestion Layer
    User -->|4. Submits Contact Form via JS POST| APIGateway

    subgraph Serverless Backend Processing
        APIGateway[🚪 Amazon API Gateway <br> HTTP API Route: /contact]:::aws
        Lambda[⚡ AWS Lambda Function <br> Python 3.x Logic Engine]:::aws
        SES[📬 Amazon SES <br> Simple Email Service]:::aws
        
        APIGateway -->|Enforces CORS & Passes Payload| Lambda
        Lambda -->|Sanitizes Data & Triggers| SES
    end

    %% Final Target
    AdminEmail[📩 Verified Target Inbox <br> pandeyankush8959@gmail.com]:::client
    SES -->|5. Delivers Form Data Mail| AdminEmail

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
