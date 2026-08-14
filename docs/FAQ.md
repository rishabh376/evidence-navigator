# FAQ - evidence-navigator

**Q: What problem does this actually solve?**
A: Security Reviewers coordinate quarantine risky artifacts for signed container releases, so audit packets are ready before review day.

Pain point: Secret rotation depends on calendar reminders and late-night manual checks.

**Q: Free to run?**
A: Yep. GCP Free Tier - $0/mo. See `terraform/INFRA_REQUIREMENTS.md`

**Q: Production ready?**
A: Yes - SLOs, security hardening, DR runbook, Helm, Terraform, monitoring.

**Q: Stack?**
A: Go, OPA Gatekeeper, Vault, Trivy, Cosign, Falco

**Q: What infra do I need?**
A: `terraform/INFRA_REQUIREMENTS.md` has the full breakdown - CPU/RAM/storage/network/cost.
