# evidence-navigator

> Security Reviewers coordinate quarantine risky artifacts for signed container releases, so audit packets are ready before review day.

**Domain:** devsecops | **Complexity:** intermediate | **Stack:** Go, OPA Gatekeeper, Vault, Trivy, Cosign, Falco

| | |
|---|---|
| Use case | Security Reviewers coordinate quarantine risky artifacts for signed container releases, so audit packets are ready before review day. |
| Pain point | Secret rotation depends on calendar reminders and late-night manual checks. |
| Success metric | Shrink evidence collection from 3 days to 2 hours with complete owner traceability. |
| Cost | $0/mo on GCP Free Tier |

## Why this exists

Secret rotation depends on calendar reminders and late-night manual checks.. Security Reviewers coordinate quarantine risky artifacts for signed container releases, so audit packets are ready before review day.

> This service shifts security left with scans, signatures, and admission controls so teams can ship safely. For this implementation, the service is designed to remove the operational friction behind Security Reviewers coordinate quarantine risky artifacts for signed container releases, so audit packets are ready before review day..

## What this product does

This project ships a production-oriented service that exposes health, readiness, observability, and domain-specific endpoints for Security Reviewers coordinate quarantine risky artifacts for signed container releases, so audit packets are ready before review day.. The implementation is intended to be deployed behind Kubernetes with secure defaults, CI validation, and rollback-ready manifests.

## Quick start

```bash
docker build -t evidence-navigator:local .
docker run -p 8080:8080 evidence-navigator:local
curl http://localhost:8080/healthz
```

## Architecture

```
GitHub CI -> Container Registry -> Kubernetes -> Go -> Operators / SRE
```

See `docs/ARCHITECTURE.md`

## Infrastructure

Full spec: `terraform/INFRA_REQUIREMENTS.md`

TL;DR: K8s cluster, 2-10 pods HPA, $0 on GCP Free Tier

## Docs

- `docs/ARCHITECTURE.md` - components, tradeoffs
- `docs/DESIGN_DISCUSSION.md` - how we decided to build this
- `docs/DEPLOYMENT.md` - GitOps, rollback
- `docs/SECURITY.md` - threat model
- `docs/TROUBLESHOOTING.md` - 3am runbook
- `terraform/INFRA_REQUIREMENTS.md` - **infra: CPU/RAM/storage/cost**

Interview prep: `interview/`
