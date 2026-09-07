---
title: We cut our EKS bill 43% and nobody noticed
kicker: FinOps
dek: >-
  A Lagos fintech moved every stateless workload onto Karpenter spot pools over
  six weeks. The savings were real; the interesting part was the guardrails that
  kept latency flat while they did it.
author: Chinedu Eze
publishedAt: 2026-09-02
---

The bill was ₦41m a month across three clusters, and roughly a third of it was
capacity nobody had asked for since 2024. The first move was not technical: we
published the per-team cost breakdown in the same channel where deploys are
announced.

Karpenter replaced two managed node groups. Consolidation is aggressive by
default, so we set a 45-second termination grace period and required pod
disruption budgets on anything with an SLO. Three services failed that check on
day one, which was the point.

Spot interruption rate in eu-west-1 sat at 4.1% for our instance families. With
a diversified pool of eleven types the practical impact was two rescheduled pods
a day. p99 latency moved by 6ms, inside normal variance.

What we would do differently: tag before you tune. Half the first month was
spent arguing about which team owned which namespace, and no dashboard can
settle that for you.
