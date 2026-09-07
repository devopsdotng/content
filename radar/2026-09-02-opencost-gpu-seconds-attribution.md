---
title: OpenCost adds GPU-seconds attribution per namespace
kind: tool
date: 2026-09-02
tags: [finops, ai]
sourceUrl: https://opencost.io/
by: amaka-obi
pr: "#407"
---

The exporter now reads DCGM metrics directly and emits per-namespace GPU-second
cost, which closes the gap that made shared accelerator pools impossible to bill
fairly.

> Answers the most-voted FinOps question on this site almost exactly.
