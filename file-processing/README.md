# File Processing - Ingestion Pipeline

A file processing pipeline that validates, parses, transforms, and summarizes file data — demonstrating sequential task orchestration with retry handling.

## What you'll learn

- Sequential multi-step file processing
- Data validation and transformation patterns
- Retry configuration with exponential backoff

## Workflow structure

```
processFileBatch (orchestrator, parallel)
  └── processSingleFile          (per-file)
      ├── readCsvFile / readJsonFile / readTextFile         (read)
      └── analyzeCsvData / analyzeJsonStructure / analyzeTextContent  (analyze)

generateConsolidatedReport (standalone, takes processFileBatch output)
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
