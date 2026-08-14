# Deployment - evidence-navigator

**Use case:** Security Reviewers coordinate quarantine risky artifacts for signed container releases, so audit packets are ready before review day.

## Infra requirements
→ `terraform/INFRA_REQUIREMENTS.md` - CPU/RAM/storage/network/cost breakdown

## GitOps
Flux watches `main` and reconciles changes automatically.

## Rollback
```
./scripts/rollback.sh
kubectl rollout undo deploy/evidence-navigator -n evidence-navigator
```
Usually < 30 sec.

## Cost
GCP Free Tier - $0/mo

The focus is supply-chain hardening: SBOMs, Cosign signatures, and policy enforcement across build and deploy.
