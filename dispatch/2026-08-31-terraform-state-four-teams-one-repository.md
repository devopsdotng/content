---
title: Terraform state, four teams, one repository
kicker: Platform
dek: >-
  Splitting a monolithic state file without a maintenance window, and the two
  mistakes that cost us a weekend.
author: Fatima Bello
publishedAt: 2026-08-31
---

A single state file had grown to 4,200 resources. Every plan took eleven minutes
and every apply was a negotiation between four teams.

We moved in slices by using moved blocks and state mv in the same change, then
froze the source of truth for exactly one hour per slice.

The first mistake was assuming import would preserve lifecycle ignore_changes
rules. It does not. The second was running the migration on a Friday.
