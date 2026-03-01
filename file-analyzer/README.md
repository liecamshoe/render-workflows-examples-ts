# File Analyzer - Two-Service Architecture

A two-service example demonstrating how an API gateway can trigger workflow tasks remotely. An Express API service accepts CSV file uploads and dispatches analysis to a separate workflow service using the Render Client SDK.

## What you'll learn

- Two-service architecture (API service + workflow service)
- Using the Render Client SDK (`Render` class) to trigger tasks remotely
- File upload handling with Express and Multer
- Error handling with `ClientError` and `ServerError`

## Architecture

```
User → API Service (Express) → Render API → Workflow Service
         ├── POST /analyze           └── analyzeFile (task)
         └── POST /analyze-task/:name
```

### API Service (`api-service/`)

An Express web server that:
- Accepts CSV file uploads via `POST /analyze`
- Calls `client.workflows.runTask()` to trigger analysis on the workflow service
- Returns results to the caller

### Workflow Service (`workflow-service/`)

A workflow service that:
- Defines the `analyzeFile` task for CSV analysis
- Parses CSV data, computes column statistics, and detects data quality issues

## Prerequisites

- A [Render API key](https://render.com/docs/api)
- Both services deployed on Render

## Setup

### Workflow Service

```bash
cd workflow-service
npm install
npm run build
npm start
```

### API Service

```bash
cd api-service
cp .env.example .env
# Edit .env: set RENDER_API_KEY and WORKFLOW_SERVICE_SLUG
npm install
npm run build
npm start
```

## Sample files

The `sample_files/` directory contains example CSV files for testing:
- `sales_data.csv` — sales transaction data
- `customer_data.csv` — customer information data

## Deploy to Render

Deploy both services:

1. **Workflow Service** — Create a **Workflow** service
   - **Build command:** `cd workflow-service && npm install && npm run build`
   - **Start command:** `cd workflow-service && npm start`

2. **API Service** — Create a **Web Service**
   - **Build command:** `cd api-service && npm install && npm run build`
   - **Start command:** `cd api-service && npm start`
   - **Environment variables:**
     - `RENDER_API_KEY` — your Render API key
     - `WORKFLOW_SERVICE_SLUG` — the slug of the workflow service
