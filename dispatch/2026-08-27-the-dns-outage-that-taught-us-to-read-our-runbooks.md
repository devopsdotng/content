---
title: The DNS outage that taught us to read our own runbooks
kicker: Incident
dek: >-
  Ninety minutes of partial failure, a runbook that referenced a decommissioned
  bastion, and what we changed the week after.
author: Amaka Obi
publishedAt: 2026-08-27
---

The trigger was mundane: a CoreDNS config map rolled out with a stale upstream.
The recovery was slow because the runbook told us to ssh somewhere that no
longer exists.

We now test the first three commands of every critical runbook monthly, in a
chaos window, with the on-call engineer who did not write it.
