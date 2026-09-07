---
title: Kubernetes 1.34 moves in-place pod resize to stable
kind: release
date: 2026-09-04
tags: [kubernetes, finops]
sourceUrl: https://kubernetes.io/blog/
by: emeka-nnaji
pr: "#412"
---

Vertical resize of CPU and memory without recreating the pod is now on by
default. The resize subresource is stable and the old feature gate is a no-op.

> Ends the restart-to-rightsize dance that made VPA unusable for stateful
> services.
