---
title: An LLM gateway that pays for itself
kicker: Applied AI
dek: >-
  Routing, caching and per-team budgets in front of three model providers,
  built in a fortnight, mostly with things we already ran.
author: Tunde Alabi
publishedAt: 2026-08-29
---

Every team had its own API key and its own idea of what a reasonable spend
looked like. The gateway exists so that conversation happens once.

Semantic caching on embeddings knocked 22% off request volume. Cheap-model-first
routing with an escalation rule handled another 31%.

Budgets are enforced at the namespace level and surface in the same cost
dashboard as compute, which is the only reason anyone looks at them.
