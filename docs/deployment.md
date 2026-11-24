# Deployment & Cluster Setup Guide

## Local integration stack

Copy `.env.example` to `.env` and set `DT_RAM_API_KEY`,
`DT_RAM_SERVICE_TOKEN`, and `POSTGRES_PASSWORD` before running Compose.

Validate the complete service graph without starting workloads:

```text
docker compose -f infrastructure/docker/docker-compose.yml config
docker compose -f infrastructure/docker/docker-compose.yml build
```

The default stack includes the Node gateway/experiment services, Go
telemetry/twin/controller services, prediction API/collector, simulation, and
safety. The RL CLI is opt-in through the `experiments` Compose profile and
does not expose a Jupyter server.

The approval path is shadow-only. Safety publishes an acknowledged
`dt.decisions.resource` event with `dry_run=true`; the Go controller audits it
without changing Kubernetes. Do not enable live actuation until rollback,
placement verification, and production model/policy validation exist.

## Kubernetes and K3s

The manifests under `infrastructure/kubernetes/` cover namespace/RBAC, NATS,
Redis, and the Go services. The k3d/K3s topology is configured in
`infrastructure/k3s/k3d.yaml`. Follow the [infrastructure guide](../infrastructure/README.md)
and [testbed runbook](../infrastructure/testbed/README.md) for deployment steps.

Prometheus is included in the local Compose stack, with configuration under
`infrastructure/monitoring/prometheus.yml`. Kubernetes monitoring manifests
and a Grafana deployment are not provided.
