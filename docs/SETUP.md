# Setup - evidence-navigator

Security Reviewers coordinate quarantine risky artifacts for signed container releases, so audit packets are ready before review day.

1. **Infra first**: `cd terraform && terraform init && terraform apply`
2. `kubectl apply -k k8s/ -n evidence-navigator`
3. `kubectl port-forward svc/evidence-navigator 8080:80 -n evidence-navigator`
4. `curl localhost:8080/healthz`

Env vars: `PORT=8080`, `LOG_LEVEL=info`

Runtime detection and telemetry let us prove the security controls are actually working in prod.
