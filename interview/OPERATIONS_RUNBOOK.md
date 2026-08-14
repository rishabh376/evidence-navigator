# Operations Runbook - evidence-navigator

Security Reviewers coordinate quarantine risky artifacts for signed container releases, so audit packets are ready before review day.

**On-call? Read this first.**

## Deploy
```
kubectl apply -k k8s/ -n evidence-navigator
kubectl rollout status deploy/evidence-navigator -n evidence-navigator
```

## Rollback (when things go red)
```
./scripts/rollback.sh
# usually < 30sec
```

## Scale up NOW
```
kubectl scale deploy/evidence-navigator --replicas=10 -n evidence-navigator
```

## Logs
```
kubectl logs -l app=evidence-navigator -n evidence-navigator -f --tail=200
```

## Crashloop?
```
kubectl describe pod -l app=evidence-navigator -n evidence-navigator
kubectl logs <pod> --previous -n evidence-navigator
```
90% of the time: missing env var in ConfigMap.

## Metrics
`curl localhost:8080/metrics` or Grafana dashboard in `monitoring/`

## DR / Failover
See `docs/DISASTER_RECOVERY.md` - RTO 15m

We actually tested this. 11 min.
