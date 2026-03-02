# Data Pipeline - Multi-Source Data Enrichment

A data pipeline that fetches from multiple sources, enriches user profiles with transaction and engagement data, segments users, and generates analytics reports.

## What you'll learn

- Parallel data fetching from multiple sources
- Data enrichment and user segmentation
- Report generation from processed data
- Retry configuration with exponential backoff

## Workflow structure

```
runDataPipeline (orchestrator)
  ├── fetchUserData          (source, parallel)
  ├── fetchTransactionData   (source, parallel)
  ├── fetchEngagementData    (source, parallel)
  ├── transformUserData      (transform)
  │   ├── calculateUserMetrics (per-user, parallel)
  │   └── enrichWithGeoData    (per-user, parallel)
  └── aggregateInsights      (output)
```

## Run locally

```bash
npm install
npm run build
npm start
```

## Deploy to Render

Create a new **Workflow** service on Render:

- **Build command:** `npm install && npm run build`
- **Start command:** `npm start`
