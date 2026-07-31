---
name: Run an autoscaling inference cluster
description: Stand up an autoscaling cluster that serves a container image behind an endpoint, scale it, and tear it down.
api: OpenRelay API (control-plane)
base_url: https://api.openrelay.inc
auth: Authorization Bearer vl_... (org-scoped API key)
operations:
  - createCluster
  - getClusterDetail
  - scaleCluster
  - restartCluster
  - stopCluster
  - terminateCluster
---

# Run an autoscaling inference cluster

Serve a model container behind an OpenRelay endpoint and manage its replicas.

## Steps

1. **Create the cluster.** Call `createCluster` (`POST /v1/orgs/{orgId}/clusters/create`) with the container image, GPU model, and replica count.
2. **Confirm health.** Poll `getClusterDetail` (`GET /v1/clusters/{id}/detail`) for replicas and GPU model until the cluster is running. Subscribe to webhooks (`cluster.running`, `cluster.degraded`, `cluster.failed`, `replica.healthy`, `replica.unhealthy`) for push updates instead of polling.
3. **Scale to load.** Call `scaleCluster` (`POST /v1/clusters/{id}/scale`) to change the replica count.
4. **Recover.** Call `restartCluster` (`POST /v1/clusters/{id}/restart`) if replicas degrade.
5. **Wind down.** Call `stopCluster` (`POST /v1/clusters/{id}/stop`) to pause, or `terminateCluster` (`POST /v1/clusters/{id}/terminate`) to delete.

## Conventions

- Webhook deliveries are signed HMAC-SHA256 in `X-VectorLay-Signature`; verify over the raw body before parsing.
- `terminateCluster` is destructive — confirm first.
- Errors return `{error, code}`; retry idempotent calls on `429`/`5xx` with backoff.
