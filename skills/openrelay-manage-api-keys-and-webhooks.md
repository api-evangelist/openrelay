---
name: Manage API keys and webhooks
description: Mint and revoke org API keys, and register signed webhooks for cluster/VM lifecycle events.
api: OpenRelay API (control-plane)
base_url: https://api.openrelay.inc
auth: Authorization Bearer vl_... (org-scoped API key)
operations:
  - createOrgApiKey
  - listOrgApiKeys
  - revokeOrgApiKey
  - createOrgWebhook
  - listOrgWebhooks
  - toggleOrgWebhook
  - regenerateOrgWebhookSecret
  - listOrgWebhookDeliveries
---

# Manage API keys and webhooks

Provision programmatic access and event notifications for an organization.

## Steps

1. **Create a key.** Call `createOrgApiKey` (`POST /v1/orgs/{orgId}/api-keys/create`). The plaintext `vl_...` key is returned once — store it immediately.
2. **Audit keys.** Call `listOrgApiKeys` (`GET /v1/orgs/{orgId}/api-keys`) for metadata (no secrets); `revokeOrgApiKey` (`DELETE /v1/orgs/{orgId}/api-keys/{id}`) to rotate.
3. **Register a webhook.** Call `createOrgWebhook` (`POST /v1/orgs/{orgId}/webhooks/create`) with a URL and event list (e.g. `vm.running`, `cluster.failed`). The signing secret is returned once.
4. **Verify deliveries.** On receipt, compute `sha256=hex(HMAC_SHA256(SHA-256(secret), rawBody))` and constant-time compare against `X-VectorLay-Signature` before parsing.
5. **Operate.** Use `toggleOrgWebhook` to enable/disable, `regenerateOrgWebhookSecret` to rotate, and `listOrgWebhookDeliveries` to inspect recent attempts (dedupe on `X-VectorLay-Delivery`).

## Conventions

- Secrets (API keys, webhook signing secrets) are shown exactly once — never fetchable again.
- Failed webhook deliveries retry 3 times (~10s, 60s, 300s).
- Errors return `{error, code}`; `403` means the key lacks scope or targets a different org.
