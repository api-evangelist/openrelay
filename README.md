# OpenRelay

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

OpenRelay is a Y Combinator-backed distributed GPU cloud for production AI inference — "the CDN of inference." It runs a global mesh of GPUs (RTX 4090/5090, A100, H100) that teams reach through a single API: rent dedicated GPU VMs with SSH and persistent volumes, stand up autoscaling inference clusters behind an endpoint, or call hosted open models via an OpenAI-compatible (and Anthropic Messages-compatible) API. Anyone can also join as a provider and earn on idle compute. The control-plane REST API (api.openrelay.inc) manages orgs, VMs, clusters, snapshots, billing, usage, transfers, provider nodes, batches, files, and webhooks, and is fully driveable from the first-party `orl` CLI — which also ships an official MCP server for agents. Traffic reroutes across healthy nodes in milliseconds, with pricing OpenRelay claims is up to 90% cheaper than the hyperscalers.

**Areas:** Company · GPU · Inference · Artificial Intelligence · Machine Learning · Cloud Compute · Infrastructure · OpenAI-Compatible · GPU Cloud · LLM

## OpenRelay on APIs.io

Everything profiled for OpenRelay is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/openrelay/](https://apis.io/providers/openrelay/)** — or go straight to one of the APIs or properties below.

### APIs (19)

- [OpenRelay Inference API](https://apis.io/apis/openrelay/openrelay-inference-api/) — OpenAI-compatible chat completions API (POST /v1/chat/completions) and, for supporting models, an Anthropic-compatible Messages API (POST /v1/messages).…
- [OpenRelay Account API](https://apis.io/apis/openrelay/openrelay-account-api/) — The signed-in user: profile, memberships, and first-time onboarding.
- [OpenRelay API Keys API](https://apis.io/apis/openrelay/openrelay-api-keys-api/) — Programmatic access keys (vl_…) used to authenticate with this API.
- [OpenRelay Batches API](https://apis.io/apis/openrelay/openrelay-batches-api/) — Batch inference jobs: submit a JSONL file of requests, poll status, and download results at a discounted rate. Served by the inference endpoint…
- [OpenRelay Billing API](https://apis.io/apis/openrelay/openrelay-billing-api/) — Prepaid balance, saved cards, deposits, and auto-recharge.
- [OpenRelay Catalog API](https://apis.io/apis/openrelay/openrelay-catalog-api/) — Public catalog: GPU models, availability, pricing, templates, and locations.
- [OpenRelay Clusters API](https://apis.io/apis/openrelay/openrelay-clusters-api/) — Autoscaling inference clusters that serve a container image behind an endpoint.
- [OpenRelay Files API](https://apis.io/apis/openrelay/openrelay-files-api/) — Input and result files for the Batch API (JSONL, up to 200 MB and 50,000 records). Served by the inference endpoint (inference.openrelay.inc).
- [OpenRelay Internal API](https://apis.io/apis/openrelay/openrelay-internal-api/) — Machine-to-machine endpoints used by platform infrastructure. Not part of the public API.
- [OpenRelay Organizations API](https://apis.io/apis/openrelay/openrelay-organizations-api/) — Organizations and their members. Most resources are scoped to an org.
- [OpenRelay Provider API](https://apis.io/apis/openrelay/openrelay-provider-api/) — For GPU providers: applications, nodes, provisioning tokens, and earnings.
- [OpenRelay Registry Credentials API](https://apis.io/apis/openrelay/openrelay-registry-credentials-api/) — Private container-registry credentials for pulling images.
- [OpenRelay Runners API](https://apis.io/apis/openrelay/openrelay-runners-api/) — Managed GitHub Actions runner pools.
- [OpenRelay Snapshots API](https://apis.io/apis/openrelay/openrelay-snapshots-api/) — Point-in-time VM snapshots and forking new VMs from them.
- [OpenRelay SSH Keys API](https://apis.io/apis/openrelay/openrelay-ssh-keys-api/) — Org-level SSH public keys that can be attached to VMs.
- [OpenRelay Transfers API](https://apis.io/apis/openrelay/openrelay-transfers-api/) — Move resources between organizations you belong to.
- [OpenRelay Usage API](https://apis.io/apis/openrelay/openrelay-usage-api/) — Current-period usage and cost breakdowns.
- [OpenRelay Webhooks API](https://apis.io/apis/openrelay/openrelay-webhooks-api/) — Subscribe to platform events with signed HTTP callbacks.
- [OpenRelay V Ms API](https://apis.io/apis/openrelay/openrelay-vms-api/) — GPU virtual machines: lifecycle, disks, SSH access, and console links.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Openrelay Webhooks](https://apis.io/asyncapis/openrelay/openrelay-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [OpenRelay MCP Server](https://apis.io/servers/openrelay/openrelay-mcp-server/)

#### Collections (18)

Postman and Open Collection request collections.

- [OpenRelay Account API](https://apis.io/collections/openrelay/open-openrelay-account-api/)
- [OpenRelay Account API Keys API](https://apis.io/collections/openrelay/open-openrelay-api-keys-api/)
- [OpenRelay Account Batches API](https://apis.io/collections/openrelay/open-openrelay-batches-api/)
- [OpenRelay Account Billing API](https://apis.io/collections/openrelay/open-openrelay-billing-api/)
- [OpenRelay Account Catalog API](https://apis.io/collections/openrelay/open-openrelay-catalog-api/)
- [OpenRelay Account Clusters API](https://apis.io/collections/openrelay/open-openrelay-clusters-api/)
- [OpenRelay Account Files API](https://apis.io/collections/openrelay/open-openrelay-files-api/)
- [OpenRelay Account Internal API](https://apis.io/collections/openrelay/open-openrelay-internal-api/)
- [OpenRelay Account Organizations API](https://apis.io/collections/openrelay/open-openrelay-organizations-api/)
- [OpenRelay Account Provider API](https://apis.io/collections/openrelay/open-openrelay-provider-api/)
- [OpenRelay Account Registry Credentials API](https://apis.io/collections/openrelay/open-openrelay-registry-credentials-api/)
- [OpenRelay Account Runners API](https://apis.io/collections/openrelay/open-openrelay-runners-api/)
- [OpenRelay Account Snapshots API](https://apis.io/collections/openrelay/open-openrelay-snapshots-api/)
- [OpenRelay Account SSH Keys API](https://apis.io/collections/openrelay/open-openrelay-ssh-keys-api/)
- [OpenRelay Account Transfers API](https://apis.io/collections/openrelay/open-openrelay-transfers-api/)
- [OpenRelay Account Usage API](https://apis.io/collections/openrelay/open-openrelay-usage-api/)
- [OpenRelay Account VMs API](https://apis.io/collections/openrelay/open-openrelay-vms-api/)
- [OpenRelay Account Webhooks API](https://apis.io/collections/openrelay/open-openrelay-webhooks-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Openrelay Openapi Overlay](https://apis.io/overlays/openrelay/openrelay-openapi-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Openrelay Authentication](https://apis.io/security/openrelay/openrelay-authentication/)
- [Openrelay Domain Security](https://apis.io/security/openrelay/openrelay-domain-security/)
- [Openrelay Vulnerability Disclosure](https://apis.io/security/openrelay/openrelay-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Openrelay Plans Pricing](https://apis.io/plans/openrelay/openrelay-plans-pricing/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.openrelay.inc/)
- [Documentation](https://docs.openrelay.inc)
- [Getting started](https://docs.openrelay.inc/docs/quickstart)
- [API reference](https://docs.openrelay.inc/docs/account/overview)
- [Pricing](https://openrelay.inc/pricing)
- [Sign up](https://app.openrelay.inc/get-started)
- [Support](https://forum.openrelay.inc)
- [Blog](https://openrelay.inc/blog)
- [Terms of service](https://openrelay.inc/terms)
- [Privacy policy](https://openrelay.inc/privacy)
- [GitHub](https://github.com/OpenRelayInc)
- [Status](https://openrelay.inc/status)

## API Evangelist rating

**Kin Score 55.2** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.7 |
| Contract quality | 52.8 |
| Contract governance | 4.5 |
| Operational transparency | 52.6 |
| Developer ergonomics | 56.5 |
| Access clarity | 71.1 |

**Agent readiness 40.4** — agent-native

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | documented (partial credit) |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | verified |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | — |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 32.7** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/openrelay/](https://apis.io/providers/openrelay/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for OpenRelay: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/openrelay/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
