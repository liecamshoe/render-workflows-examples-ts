# ETL Job - Extract, Transform, Load Pipeline

A structured ETL pipeline demonstrating data extraction from multiple sources, transformation with business rules, and loading into a destination — with built-in retry handling.

## What you'll learn

- Multi-step task orchestration (extract → transform → load)
- Retry configuration with exponential backoff
- Error handling in workflow tasks

## Workflow structure

```
runETLPipeline (orchestrator)
  ├── extractOrders      (extract from source)
  ├── extractInventory   (extract from source)
  ├── transformData      (apply business rules)
  └── loadData           (write to destination)
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
