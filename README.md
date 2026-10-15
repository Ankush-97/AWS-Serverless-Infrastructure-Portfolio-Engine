# 🚀 Production-Grade AWS Infrastructure Portfolio (`ankush.fun`)

A high-performance, enterprise-grade personal portfolio platform engineered on **AWS Infrastructure**. The frontend application runs on an **AWS EC2 Instance Layer** powered by an Apache web server, featuring automated **Let's Encrypt SSL/TLS encryption**. The contact system leverages a fully asynchronous, serverless, spam-protected event injection pipeline engineered via **AWS Lambda**, **Amazon API Gateway**, and **Amazon Simple Email Service (SES)**.

---

## 🏗️ Architectural Infrastructure Workflow Design

This architecture diagram illustrates the end-to-end data pipeline traffic routing matrix across the application platform, handling standard user sessions and asynchronous contact ingest vectors securely:

```text 
                                                      [ USER BROWSER CLIENT ]
                                                              │
                                                  (DNS Lookup for ankush.fun)
                                                              │
                                                              ▼
                                                       [ AWS Route 53 ]
                                                  (Authoritative Nameservers)
                                                              │
                                                     (Returns Public IP)
                                                              ▼
                      ┌──────────────────────── AWS Cloud Inbound Security Layer ─────────────────────────┐
                      │                                                                                   │
                      │    [ HTTP/HTTPS Requests ] ──(Port 80/443 Allow)──> [ EC2 Inbound Security GP ]   │
                      │                                            │                                      │
                      └───────────────────────────────────────────────────────────────────-───────────────┘
                                                                   ▼
                                                      [ APACHE WEB SERVER LAYER ]
                                                      - Host: AWS EC2 Instance
                                                      - Domain: https://ankush.fun
                                                      - Certbot Managed SSL/TLS
                                                                   │
                                                          (User Form Submit)
                                                                   │
                                                                   ▼
                                                      [ AMAZON API GATEWAY HTTP ]
                                                      - CORS Rule Handshake (*)
                                                      - Method Route: POST /default
                                                                   │
                                                            (JSON Ingestion)
                                                                   │
                                                                   ▼
                                                      [ AWS LAMBDA ENDPOINT ]
                                                      - Runtime: Python 3.12 Engine
                                                      - Single Execution Constraint
                                                      - Concurrency / Retry = 0
                                                                   │
                                                          (Filtered Payload)
                                                                   │
                                                                   ▼
                                                      [ AMAZON SES COMPONENT ]
                                                      - Region: ap-south-1 (Mumbai)
                                                      - Sender Identity Verification
                                                                   │
                                                           (Email Delivery)
                                                                   │
                                                                   ▼
                                                      [ VERIFIED TARGET GMAIL ]
                                                      (Secure Developer Inbox 📩)
```


---

## 🛠️ Deep-Dive Technical Implementation Matrix

### 1. Authoritative DNS & Domain Mapping (AWS Route 53)
- **Domain Registry Routing:** Transferred active namespace authorization controllers for `ankush.fun` from external registrars directly over onto an **AWS Route 53 Hosted Zone**.
- **DNS Record Mapping Infrastructure:**
  - `A Record` -> Points the root domain (`ankush.fun`) directly to the EC2 Public IPv4 target host address (`AWS EC2 Public-IP`).
  - `A Record (www)` -> Maps canonical web requests (`www.ankush.fun`) to route synchronously through identical IP bindings.
  - `NS/SOA Records` -> Automatically populated with AWS DNS authoritative server clusters (`://ahrdns-xx.com`) across multiple availability zones.

### 2. Host Compute Web Infrastructure (AWS EC2 & Apache)
- **Deployment Platform:** Virtual machine provisioned within a secure VPC subnetwork topology. Inbound routing constraints are guarded via strict network security firewalls explicitly enabling ports `80` (HTTP) and `443` (HTTPS) globally (`0.0.0.0/0`).
- **Server Engine Configuration:** Configured Apache HTTP web engine hosting multi-layered local file deployment structures inside directory `/var/www/html/`.
- **SSL/TLS Automated Encryption:** Configured the **Certbot Agent** to run against the Apache site virtual host rules, executing a challenge handshake validation loop with **Let's Encrypt CA** to provision instant wildcard-ready HTTPS validation.

### 3. Serverless Event Ingestion Backend (AWS Lambda & API Gateway)
- **Decoupled API Endpoint Vector:** Form actions route asynchronously through an Amazon API Gateway REST layer, executing cross-origin preflight handshakes (`CORS`) automatically matching wildcards (`*`) to eliminate security blockages across standard browser runtimes.
- **Serverless Compute Logics:** The ingestion engine is fully asynchronous and leverages **Python 3.12** inside an AWS Lambda function execution sandbox.
- **Data Sanitization & Ingestion Security Rule:**
  - Implements custom runtime regex trimming logic to catch empty string variants or duplicate parsing blocks (`N/A` text overrides).
  - Skews serverless timeout thresholds down by matching a hard operational constraint of **`0` Retry attempts** inside asynchronous trigger parameters to bypass asynchronous looping patterns.

### 4. Downstream Mail Delivery Processing (AWS SES)
- **Identity Ingestion Pipeline:** Verified individual endpoint target permissions for identity identifier `pandeyankush8959@gmail.com` matching secure sandbox specifications.
- **Delivery Framework:** Automatically compiles sanitized data feeds incoming from the backend computational layers and processes downstream outbound delivery calls using Amazon SES endpoints over secure transport layers.

## 📊 Infrastructure Monitoring & Enterprise Observability (Datadog)

To maintain system reliability and audit operational parameters, the entire platform topology is bound to the **Datadog Cloud Observability Framework**.

### 🛠️ Why Datadog Integration Was Implemented?
1. **Real-Time Infrastructure Visualization:** To prevent application crashes by proactively logging hardware load abnormalities (such as sudden CPU usage skews or Memory bottlenecks on the EC2 kernel).
2. **Asynchronous Log Aggregation:** Standard terminal logging structures make auditing difficult. Datadog extracts raw Apache traffic strings and parses them into a centralized, graphical geo-analytics map.
3. **Proactive Troubleshooting & Performance Guarding:** Acts as an enterprise runtime doctor by measuring document object load speeds and reporting processing delivery latencies immediately.

### ⚙️ How Datadog Integration Was Programmed?
- **Step 1: Kernel Layer Instrumentation**  
  Deployed the native **Datadog Agent (v7)** agent system engine directly onto the Ubuntu host architecture loop via an automated installer daemon mapping encrypted account api tokens.
- **Step 2: Log Collection Pipeline Activation**  
  Modified the main core cluster config (`/etc/datadog-agent/datadog.yaml`) to switch system wide log processing active by specifying:
  ```yaml
  logs_enabled: true
  ```
- **Step 3: Web Server Interface Configuration**  
  Cloned the explicit Apache logging parser blueprint and built a secure pathway targeting local file streams:
  ```bash
  sudo cp /etc/datadog-agent/conf.d/apache.d/conf.yaml.example /etc/datadog-agent/conf.d/apache.d/conf.yaml
  ```
  Mapped telemetry configuration arrays to track inbound traffic structures routing straight through target file paths inside the host operating filesystem layout: `/var/log/apache2/access.log`.

---

## 🔍 In-Depth Engineering Troubleshooting Log

#### 1. Symptom: Frontend Handshake Termination / "Unable to connect to the server" Error
- **Root Cause Analytical Breakdown:** The host application engine running inside browser instances performs an automatic cross-site pre-flight request evaluation block before launching a payload transfer session. If the ingestion resource interface layers (API Gateway) fail to reply with adequate header properties during the network connection handshake, browser instances explicitly isolate the execution path via a strict security blockage.
- **System Remediation Action Path:** Navigate straight to your Amazon API Gateway Management Console. Select the active route gateway `ContactFormHandler-API`. Click into the **CORS** section tab, then select **Configure**. Modify properties by matching Access-Control-Allow-Origin parameters to wildcard target `*`, specify target authentication execution methods bound exactly to `POST` and `OPTIONS`, and register header parameters as `content-type`. Click **Save** and deploy the revised architecture pipeline configuration state down into the active deployment distribution lifecycle target `$default`.

#### 2. Symptom: Redundant Duplicated Outbound Mail Dispatch Triggers
- **Root Cause Analytical Breakdown:** AWS Lambda functions operating in asynchronous orchestration environments use built-in fault-tolerant execution engines. If an asynchronous backend workflow takes slightly longer to reply to a request during heavy traffic, the internal network loop automatically fires sequential fallback attempts. This creates a multi-trigger processing pattern that can result in 3 to 4 duplicate tracking alerts for a single form click.
- **System Remediation Action Path:** Open your target function view layout within the AWS Lambda Dashboard. Click into the **Configuration** property tab, navigate to the **Asynchronous invocation** submenu resource line, and locate the parameters tracking active fault-tolerance variables. Select **Edit** on the interface panel layout, change the default retry attempt variable parameter count from an active value of `2` down onto a precise structural value constraint of **`0`**, and save the updated configuration state.

#### 3. Symptom: High Latency Penalties / Document Object Model Loading Skews (21+ Seconds Lag)
- **Root Cause Analytical Breakdown:** Third-party package distribution mirror networks (specifically outdated configurations or blocked content delivery networks) can trigger heavy data transport lags. Browsers attempting to process un-optimized asset requests block page rendering routines during initial paint iterations until the request encounters a connection drop or network termination script timeout.
- **System Remediation Action Path:** Inspect the structural linkage dependencies across your static assets file layer using your terminal editor tool `nano index.html`. Isolate dead script calls, decouple broken dependencies, and replace flaky file links with robust enterprise mirror routes (such as Cloudflare distribution nodes). Clear system performance configurations and drop lingering web socket connections using a high-level server command flush:
  ```bash
  sudo systemctl restart apache2
  ```
  Instruct the user client layout engine to bypass previous application state storage properties using an isolated hard browser refresh routine (**`Ctrl + F5`**).
