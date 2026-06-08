# new-service

> new-service — scaffolded via the Meijer Platform Golden Path

## Overview

| Property | Value |
|---|---|
| Backend | .NET 11.0 |
| Frontend | v26.3.0 |
| Database | PostgreSQL |
| Primary Cloud | Azure |
| Secondary Cloud (DR) | GCP |
| Criticality | {{CRITICALITY}} |

## Getting Started

### Prerequisites
- Docker Desktop
- Node.js 20+ (if Node.js service) / .NET 8 SDK (if .NET service)
- Azure CLI (for cloud deployment)

### Run locally

```bash
# Install dependencies
npm install        # Node.js
# or
dotnet restore     # .NET

# Start with Docker Compose
docker compose up
```

### Environment variables

Copy `.env.example` to `.env` and fill in values:

```bash
cp .env.example .env
```

## CI/CD

This service uses GitHub Actions workflows (`.github/workflows/`):

| Workflow | Trigger | Description |
|---|---|---|
| `ci.yml` | Push / PR | Build, test, SAST scan, container scan |
| `deploy.yml` | Port self-service | Deploy to Dev / Staging / Production |

## Infrastructure

Terraform configuration is in `infrastructure/terraform/`. The module is
registered in Port at the Terraform Module property of this service.

## Observability

- **Logs**: Azure Monitor / Dynatrace
- **Metrics**: Dynatrace
- **Alerts**: PagerDuty (`{{CRITICALITY}}` criticality)
- **SLOs**: Defined in `infrastructure/dynatrace/slo.json`

---
*This service was scaffolded by the [Meijer Platform Portal](https://app.getport.io). Do not edit CI/CD templates manually — raise a platform request instead.*
