---
title: Karpenter 1.2 adds scheduled disruption budgets
kind: release
date: 2026-08-27
tags: [kubernetes, karpenter]
sourceUrl: https://karpenter.sh/
by: chinedu-eze
pr: "#394"
---

Budgets accept cron windows, so consolidation can be suppressed during business
hours without disabling it entirely. Node pools also gain a reserved-capacity
provisioning mode.

> The workaround people were scripting is now a first-class field.
