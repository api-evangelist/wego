# Wego

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

Wego (Wego Pte Ltd, Singapore, with a regional base in Dubai) is a travel metasearch engine
and online travel agency serving travelers across the Middle East, North Africa, Southeast
Asia and beyond. It compares flights and hotels across airlines, hotels and online travel
agencies, and sells Book-on-Wego inventory directly.

## API surfaces

| API | Base URL | Contract | Docs |
|---|---|---|---|
| **Wego API** (agent-native REST) | `https://api.wego.com` | OpenAPI 3.1.0, v0.19.0, 22 operations, served at [`api.wego.com/openapi`](https://api.wego.com/openapi) | [docs.wego.com](https://docs.wego.com) |
| **Wego Marketplace (Affiliate) API** | `https://affiliate-api.wego.com` | documented reference only | [developers.wego.com](https://developers.wego.com/docs/affiliate/get-started) |
| **Flight B2B Distribution API v3** | `https://api.wego.com` | documented as OpenAPI 3.0.0; the portal's spec download does not resolve | [developers.wego.com](https://developers.wego.com/docs/distribution/getting-started) |
| **Hotel B2B Distribution API** | `https://api.wego.com` | documented as OpenAPI 1.0.0; the portal's spec download does not resolve | [developers.wego.com](https://developers.wego.com/docs/distribution/getting-started) |

## Agent surfaces

Wego is unusually agent-forward for a travel company. It publishes, all first-party:

- a **remote MCP server** at `https://api.wego.com/mcp`, OAuth-protected with RFC 9728
  protected-resource metadata, RFC 8414 authorization-server metadata and dynamic client
  registration — listed in the Claude connectors directory;
- a **ChatGPT plugin** delivering the same capability;
- two **Agent Skills**, Apache-2.0, at [github.com/wego/skills](https://github.com/wego/skills)
  and `docs.wego.com/skills/agent-onboarding/SKILL.md`, saved verbatim under `skills/`;
- the **`wego` CLI** (v1.0.1), signed release binaries verified fail-closed against a
  cosign/Sigstore-backed checksum manifest;
- an **`llms.txt`** index at `docs.wego.com/llms.txt`, with every docs page also served as `.md`.

The API reference is written to double as an agent tool contract: RFC 9457 problem bodies
with a closed `code` enum, RateLimit / RateLimit-Policy headers, documented async settlement
rules, documented id expiry, and positive-witness fields.

## Known gaps

- No deprecation policy, no `Sunset`/`Deprecation` header contract, and no dated changelog —
  on a surface Wego itself labels a Research Preview.
- No status page (`status.wego.com` redirects to the consumer help centre).
- No idempotency mechanism on either `POST`, and search creation is the tightest quota.
- No `security.txt` and no published vulnerability disclosure programme.
- The Developers Portal advertises "Export OpenAPI Spec" downloads for its three B2B specs
  (`/oauth-1.0.0.yaml`, `/flight-3.0.0.yaml`, `/hotel-1.0.0.yaml`) that its own host does not
  serve — every one returns the Docusaurus SPA shell.

Full detail lives in the artifacts in this repository; `apis.yml` is the index.
