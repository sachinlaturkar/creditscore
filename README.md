Real-Time Credit Risk Engine on Google Cloud
🚀 Overview
This project is a high-performance, serverless data pipeline designed to ingest, score, and store credit transactions in real-time. Built on Google Cloud Platform (GCP), it demonstrates a "Lambda Architecture" capable of handling high-velocity data streams while providing both millisecond-latency alerts and long-term analytical insights.

🛠 Tech Stack
Infrastructure: Terraform (IaC), GitHub Actions (CI/CD).

Ingestion: Google Pub/Sub (Messaging Queue).

Processing: Apache Beam / Google Cloud Dataflow (Streaming Analytics).

Hot Storage (Speed Layer): Google Cloud BigTable (NoSQL for <10ms lookups).

Cold Storage (Batch Layer): Google BigQuery (Data Warehouse for ML and BI).

Observability: Google Cloud Monitoring & Logging.

🏗 Architecture
Ingestion: Synthetic credit transactions are streamed into Pub/Sub.

Processing: A Dataflow job (Python/Beam) consumes the stream, performing windowed analysis and risk scoring.

Risk Scoring: * Low-Risk: Routed to BigQuery for trend analysis and auditor reporting.

High-Risk: Simultaneously routed to BigTable to trigger instant fraud-prevention flags and to BigQuery for a complete record.

DevOps: The entire environment is provisioned via Terraform and deployed through GitHub Actions using Workload Identity Federation (Keyless Auth).

📈 Key Business Features
Scalability: The pipeline uses Dataflow's autoscaling to handle spikes in transaction volume.

Low Latency: High-risk flags are available in BigTable in near real-time, allowing downstream apps to block fraudulent cards instantly.

Security: Implements the principle of least privilege using custom IAM roles and OIDC-based authentication via GitHub.
