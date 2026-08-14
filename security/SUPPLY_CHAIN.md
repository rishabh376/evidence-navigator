# Supply Chain Security - evidence-navigator

Security Reviewers coordinate quarantine risky artifacts for signed container releases, so audit packets are ready before review day.

## Controls
- Trivy filesystem and image scans fail HIGH/CRITICAL findings before deploy.
- Cosign signs images in CI and Kyverno verifies signatures at admission.
- SBOM is generated in SPDX format and attached to the release artifact.
- OPA/Gatekeeper denies privileged pods and root containers.
- Vault or External Secrets handles runtime secrets; nothing sensitive is committed.

## Stack
Go, OPA Gatekeeper, Vault, Trivy, Cosign, Falco

## Interview Angle
Talk about where the gate sits: developer PR, CI scan, registry signature, Kubernetes admission, and runtime detection.
