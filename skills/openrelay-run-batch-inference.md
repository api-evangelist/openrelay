---
name: Run a batch inference job
description: Upload a JSONL input file, submit an asynchronous batch, poll to completion, and download results.
api: OpenRelay API (control-plane)
base_url: https://api.openrelay.inc
auth: Authorization Bearer vl_... (org-scoped API key)
operations:
  - presignFileUpload
  - uploadFile
  - completeFileUpload
  - createBatch
  - getBatch
  - listBatches
  - cancelBatch
  - getFileContent
---

# Run a batch inference job

Submit a large chat/text-completion job as a JSONL file and process it asynchronously.

## Steps

1. **Upload the input file.** For small files, `uploadFile` (`POST /v1/files`) directly. For large files, `presignFileUpload` (`POST /v1/files/presign`), PUT the bytes to the presigned URL, then `completeFileUpload` (`POST /v1/files/{id}/complete`) — this step is idempotent, so re-completing a registered id returns the existing file.
2. **Create the batch.** Call `createBatch` (`POST /v1/batches`) referencing the input file id. Each JSONL line carries a `custom_id` to join results back to inputs.
3. **Poll to completion.** Call `getBatch` (`GET /v1/batches/{id}`) until the status lifecycle reaches completed; use `listBatches` (`GET /v1/batches`, cursor-paginated) to enumerate jobs.
4. **Download results.** Call `getFileContent` (`GET /v1/files/{id}/content`) on the output and error files. One JSONL line per request, joined by `custom_id`.
5. **Cancel if needed.** Call `cancelBatch` (`POST /v1/batches/{id}/cancel`).

## Conventions

- List endpoints are cursor-paginated (`limit` + `cursor` -> `items` + `nextCursor`).
- Batch/file endpoints can return `429` (InferenceRateLimited) and `413` (too large); back off and honor `Retry-After`.
