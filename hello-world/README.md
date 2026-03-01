# Hello World - Getting Started with Render Workflows

The simplest possible workflow example to help you understand the basics of Render Workflows.

## What you'll learn

- **What is a task?** A function that can be executed as a workflow
- **What is a subtask?** A task called by another task using `await`
- **How to orchestrate:** Combining multiple tasks to create workflows

## Workflow structure

```
calculateAndProcess (multi-step orchestrator)
  ├── addDoubledNumbers
  │   ├── double (subtask #1)
  │   └── double (subtask #2)
  └── processNumbers
      ├── double (subtask for item 1)
      ├── double (subtask for item 2)
      └── double (subtask for item N)
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
