# cicd-assignment2 — Jenkins → Netlify Pipeline

A CI/CD pipeline exercise: a React app automatically built, tested, and deployed to Netlify through Jenkins.

## Overview

This repo is a checkpoint in a broader progression of CI/CD pipeline projects — see [Related Pipelines](#related-pipelines) below. The React app itself is intentionally minimal (a starter template displaying a name and course label); the focus is the **Jenkinsfile**, which automates the full build-test-deploy cycle.

## Pipeline Stages

1. **Build** — installs dependencies and creates the production build (`npm install && npm run build`)
2. **Test** — runs the test suite in CI mode (`npm test -- --watchAll=false`)
3. **Deploy** — deploys the built app straight to Netlify using the Netlify CLI (`netlify-cli deploy --prod`), authenticated via Jenkins-managed credentials (`NETLIFY_SITE_ID`, `NETLIFY_TOKEN`)

## Tech Stack

- **React** (Create React App)
- **Jenkins** (declarative pipeline, using a configured Node 20 tool)
- **Netlify** (deployment target, via `netlify-cli`)

## Getting Started

### Run the app locally
```bash
npm install
npm start
```
Visit [http://localhost:3000](http://localhost:3000).

### Run the pipeline
This pipeline is designed to run inside Jenkins with:
- A Jenkins-configured Node.js tool (`Node20`)
- `NETLIFY_SITE_ID` and `NETLIFY_TOKEN` configured as Jenkins credentials

## Related Pipelines

This repo is part of a progression through CI/CD concepts, each adding a new capability:

1. **`heathermayhowse`** — basic pipeline: install → build → test
2. **`cicd-assignment2`** (this repo) — adds automated deployment to Netlify
3. **`ci-demo`** — adds a Dockerized build stage and deployment to AWS S3
4. **`enterprise-computing-project`** — full pipeline: multi-stage Docker build (Nginx-served), push to AWS ECR, and deploy to ECS
