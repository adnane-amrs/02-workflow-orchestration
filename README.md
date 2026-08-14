# Module 2: Workflow Orchestration

Welcome to the **Workflow Orchestration** module of the Data Engineering Zoomcamp! This repository contains the orchestrator configuration and data pipelines built using **Kestra**.

## 🚀 What is this repository?
This folder houses the infrastructure and workflow flows required to automate data ingestion, schedule jobs, and interact with cloud resources (specifically Azure) using Kestra as the core orchestration engine.

## 🛠️ What was done in this module?

1. **Kestra Local Setup (Docker Compose)**
   - Set up Kestra locally using `docker-compose.yml` with a PostgreSQL backend database.
   - Configured Kestra to safely read Base64-encoded environment variables (passed via a `.env` file) to prevent credential leaks.

2. **Basic Data Pipelines (Flows)**
   - `01-hello-world.yaml` & `02-python.yaml`: Introductory flows to understand Kestra's syntax and Python task executions.
   - `03_getting_started_data_pipeline.yaml`: A foundational pipeline demonstrating data extraction and transformation.
   - `04_postgres_taxi.yaml` & `05_postgres_taxi_scheduled.yaml`: Workflows that download New York Taxi data, process it, and load it into a local PostgreSQL database (with scheduling).

3. **Azure Cloud Integration & Security**
   - `06-azure-kv.yaml`: Securely injected Azure Service Principal credentials (Tenant ID, Client ID, Client Secret) into Kestra's internal Key-Value (KV) store using the `secret()` function.
   - `07_azure_setup.yaml`: Automated the provisioning of Azure infrastructure! This flow logs into Azure using the securely stored credentials and uses the Azure CLI plugin to automatically create a **Resource Group**, **Storage Account**, and **Storage Container**.

4. **Security Best Practices**
   - Configured a comprehensive `.gitignore` to explicitly ignore `.env` files, cloud credential files (`*.json`, `*.pem`), and future Terraform state files, ensuring no sensitive Azure or cloud credentials are ever pushed to GitHub.

## ⚙️ How to run
1. Ensure your `.env` file is created locally (this is ignored by git for security) and contains your Base64-encoded Azure secrets:
   ```env
   SECRET_AZURE_TENANT_ID=your_base64_encoded_tenant_id
   SECRET_AZURE_CLIENT_ID=your_base64_encoded_client_id
   SECRET_AZURE_CLIENT_SECRET=your_base64_encoded_client_secret
   ```
2. Start the Kestra server:
   ```bash
   docker compose up -d
   ```
3. Navigate to `http://localhost:8080` to access the Kestra UI and execute the flows!
