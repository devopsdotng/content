# devopsdotng/content

Content repository for `devops.ng`.

One markdown file equals one published entry.

## Structure

```
content/
  dispatch/   long-form articles
  radar/      short updates
  events/     meetups, webinars, workshops
  projects/   community projects
  training/   practical sessions and clinics
```

## File naming

Use this format:

`YYYY-MM-DD-a-short-slug.md`

- Date = when the event/change/article happened
- Slug = short readable URL part

## Radar entries (`content/radar/`)

```markdown
---
title: Kubernetes 1.34 moves in-place pod resize to stable
kind: release          # release | deprecation | tool | paper | regional
date: 2026-09-04
tags: [kubernetes, finops]
sourceUrl: https://kubernetes.io/blog/2026/in-place-resize/
by: babafemi-bulugbe
pr: "#412"             # optional
---

What changed.

> Why it matters in one sentence.
```

Rules:

1. One entry per change.
2. Link primary source.
3. Include one-sentence impact.
4. No pure marketing announcements.

## Dispatch entries (`content/dispatch/`)

```markdown
---
title: We cut our EKS bill 43% and nobody noticed
kicker: FinOps         # FinOps | Platform | Applied AI | Incident | Careers
dek: One-sentence summary that earns the click.
author: Babafemi Bulugbe
publishedAt: 2026-09-02
---

Article body.
```

Notes:

- Reading time is computed automatically.
- `dek` appears on listing pages, so keep it clear and specific.

## Event entries (`content/events/`)

```markdown
---
id: evt_k8s_cost_clinic          # do not change after publish
title: "Kubernetes cost clinic: bring your bill"
city: Lagos                      # Lagos | Abuja | Port Harcourt | Virtual
venue: Zone Tech Park, Gbagada
format: Meetup                   # Meetup | Webinar | Workshop
startsAt: 2026-09-12T17:30:00+01:00
endsAt: 2026-09-12T20:30:00+01:00
capacity: 180
---

Event description.
```

Notes:

- `id` is immutable once used.
- Use `+01:00` (West Africa Time).
- Attendance is not stored in git.

## Allowed tags

```
kubernetes  finops  ai  terraform  devops
reliability ci-cd   security  opentofu  observability
```

## Validation

Run:

```bash
pnpm content:validate
```

Validation checks frontmatter shape, required fields, enums, dates, tags, URLs, slug uniqueness, and event id consistency.

## Publish flow

1. Add or update markdown file(s)
2. Run validation
3. Commit
4. Push to `main`

The site reads these folders by name, so keep the folder names in sync with the site sections.
