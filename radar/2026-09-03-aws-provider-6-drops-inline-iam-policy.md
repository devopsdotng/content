---
title: Terraform AWS provider 6.x drops the inline IAM policy attributes
kind: deprecation
date: 2026-09-03
tags: [terraform, security]
sourceUrl: https://registry.terraform.io/
by: ibrahim-sani
pr: "#409"
---

aws_iam_role.inline_policy and the matching user attribute are removed.
Migration is to aws_iam_role_policy resources, and the provider emits a
plan-time error rather than a warning.

> If your modules predate 2024 this is a breaking upgrade, not a version bump.
