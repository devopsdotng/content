---
title: Trivy and Grype converge on a shared SBOM attestation format
kind: tool
date: 2026-08-21
tags: [security, ci-cd]
sourceUrl: https://openssf.org/
by: zainab-yusuf
pr: "#384"
---

Both scanners now emit and verify the same in-toto attestation, so a signed SBOM
produced by one is consumable by the other in admission policy.

> One less bespoke conversion step in supply-chain pipelines.
