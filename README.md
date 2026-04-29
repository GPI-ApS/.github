# GPI — Governance Privacy Intelligence

**AI governance for organisations that can't afford to leak.**

GPI tokenises personally identifiable information *before* it reaches any
language model, governs document access against the source system's own
ACL, and produces a GDPR-grade audit trail of every interaction. Built in
Denmark, deployed single-tenant, self-hosted by default.

---

## What we build

**PII tokenisation, then AI.** Every piece of personal data is detected,
tokenised, and replaced with a non-reversible reference *before* any
prompt reaches a language model. The model never sees the underlying
value. Rehydration happens after the model returns, inside our trust
boundary.

**Danish-first entity recognition.** Our PII detection is built on a
custom two-stage fine-tune of XLM-R Large on the DANSK and DaNE
corpora — F1 87.6 (DANSK dev) / 93.0 (DaNE dev) — quantised to ONNX
INT8 and shipped inside the service. No third-party API calls during
detection.

**Source-system compliance.** Per-document access is governed by the
source system's own ACL — SharePoint, file shares, SQL — not by a
cached copy that drifts out of sync. If a user can't see a document at
the source, the model can't either.

**GDPR audit trail.** Every prompt, every retrieval, every model call
is recorded with the context needed to answer Article 15 (right of
access) and Article 17 (right to erasure) requests through an API,
not through ad-hoc database queries.

## Architectural stance

**Single tenant per deployment.** One installation, one customer's
data. No shared infrastructure, no noisy-neighbour failure modes, no
cross-tenant escape paths to design defences against.

**Self-hosted by default.** Customer data stays on infrastructure the
customer controls — Azure or on-premises. We do not train on customer
data, do not aggregate across customers, and do not run a multi-tenant
cloud for our customers' content to live in.

**Replaceable model layer.** We use Azure OpenAI, OpenAI, Anthropic,
or local models through a thin custom abstraction. No Semantic Kernel,
no LangChain. Customers choose which model serves their data and on
what terms.

## Where we are

GPI is built and maintained from Denmark, targeting Danish and EU
enterprises with sensitive data governance requirements. The platform
is in active development.

Most of our source lives in private repositories in this organisation.

## Get in touch

- Website: [gpi.dk](https://www.gpi.dk)
- For technical or security reviews, contact us via the website.

---

We treat our own data the way we ask our customers to treat theirs:
self-hosted analytics on our own infrastructure, no third-party
trackers, no cookies, encrypted credential vaults, no long-lived
tokens in CI.
