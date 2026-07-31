---
name: Deploy a GPU VM
description: Pick a GPU, check availability and price, launch a VM, watch its burn rate, and tear it down.
api: OpenRelay API (control-plane)
base_url: https://api.openrelay.inc
auth: Authorization Bearer vl_... (org-scoped API key)
operations:
  - listGpuModels
  - getGpuAvailability
  - getPricing
  - createVm
  - getVmDetail
  - getVmBurn
  - stopVm
  - terminateVm
---

# Deploy a GPU VM

Provision a single GPU virtual machine on OpenRelay and manage its lifecycle.

## Steps

1. **Discover GPUs.** Call `listGpuModels` (`GET /v1/gpu-models`) and `getGpuAvailability` (`GET /v1/gpu-availability`) to find an obtainable GPU type/quantity. Unsatisfiable requests are rejected immediately, so honor the returned availability.
2. **Check price.** Call `getPricing` (`GET /v1/pricing`) to confirm the bundled hourly rate for the chosen GPU.
3. **Create the VM.** Call `createVm` (`POST /v1/orgs/{orgId}/vms/create`) with the GPU model, image, and disk. Use the caller's `orgId` (resolve via `whoami`).
4. **Confirm it is running.** Poll `getVmDetail` (`GET /v1/vms/{id}/detail`) until the VM reports running; read `statusReason` if it fails.
5. **Watch cost.** Call `getVmBurn` (`GET /v1/vms/{id}/burn`) for live burn rate, session cost, and org runway to the auto-stop floor.
6. **Wind down.** Call `stopVm` (`POST /v1/vms/{id}/stop`) to pause billing, or `terminateVm` (`POST /v1/vms/{id}/terminate`) to delete it.

## Conventions

- **Errors** return `{error, code}` JSON (not RFC 9457). On `429`/`5xx`, back off with jitter and honor `Retry-After`.
- **terminateVm is destructive** and irreversible — confirm before calling.
- Some VM operations (`rebootVm`, `resizeVmDisk`) are Beta and accepted-but-not-yet-executed on the data plane.
