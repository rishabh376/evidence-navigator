# Interview Guide - evidence-navigator

**Evidence Navigator**

> Security Reviewers coordinate quarantine risky artifacts for signed container releases, so audit packets are ready before review day.

Pain: Secret rotation depends on calendar reminders and late-night manual checks.  
Impact: Shrink evidence collection from 3 days to 2 hours with complete owner traceability.  
Team: Ken (Security Engineer), Priya (Staff Architect), Marcus (Senior Dev)

---

## Whiteboard this

```
Dev -> GitHub -> CI (Trivy) -> GHCR (Cosign) -> Flux -> K8s -> Prometheus -> Grafana -> Alertmanager -> Slack
```

Walk through: commit → CI → image sign → GitOps reconcile → HPA scale → SLO alert → rollback

## Talk about

1. **Why K8s and not serverless?** Team expertise, portability, cost at scale. Cold start would kill p95.
2. **SLI/SLO** - 99.9% availability, p95 < 250ms, error budget 43m/mo. Freeze deploys <10% budget.
3. **Security** - Trivy shift-left, Cosign signed images, non-root + readOnlyRootFilesystem, NetworkPolicy default-deny, Vault secrets.
4. **Deploy strategy** - RollingUpdate now, Canary with Argo Rollouts next. Rollback <30sec.
5. **Observability** - Prometheus RED metrics, OTel traces, Loki logs, correlated in Grafana.
6. **Cost** - $0/mo on GCP Free Tier. Self-hosted Prometheus vs $800/mo Datadog.
7. **DR** - RTO 15m, RPO 1h. Tested fire drill: 11min recovered.
8. **Trade-offs we made** - see `docs/DESIGN_DISCUSSION.md` and `docs/architecture/ADR-001-runtime-choice.md`

## Infra needed

Full breakdown: `terraform/INFRA_REQUIREMENTS.md` - CPU/RAM/storage/network/dependencies/cost

## "Tell me about a time..."

- Production incident: see `interview/PRODUCTION_INCIDENTS.md`
- RCA: see `interview/ROOT_CAUSE_ANALYSIS.md`
- On-call: see `interview/OPERATIONS_RUNBOOK.md`
