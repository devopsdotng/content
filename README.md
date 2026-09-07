# Contributing content

Everything in this directory is published on [devops.ng](https://devops.ng) and
in the mobile app. One markdown file is one piece of content.

You do not need to install anything to contribute. Add a file, open a pull
request, and CI will tell you if the front matter is wrong.

```
content/
  dispatch/   long-form articles — the weekly dispatch
  radar/      short entries — what changed in the field this week
  events/     meetups, webinars and workshops
```

## Naming

`YYYY-MM-DD-a-short-slug.md`

The date is when the thing happened or was published, not when you wrote it.
The slug becomes the URL, so keep it short and readable.

---

## `content/radar/` — what's new in the field

The Radar is one entry per thing that changed. Round-ups get split.

```markdown
---
title: Kubernetes 1.34 moves in-place pod resize to stable
kind: release          # release | deprecation | tool | paper | regional
date: 2026-09-04       # when it happened
tags: [kubernetes, finops]
sourceUrl: https://kubernetes.io/blog/2026/in-place-resize/
by: emeka-nnaji        # your GitHub handle
pr: "#412"             # optional, filled in by maintainers
---

Vertical resize of CPU and memory without recreating the pod is now on by
default. The resize subresource is stable and the old feature gate is a no-op.

> Ends the restart-to-rightsize dance that made VPA unusable for stateful
> services.
```

The paragraph is what changed. The blockquote is why an engineer here should
care, in one sentence. Both are required.

### The rules

1. One entry, one thing that changed. Round-ups get split.
2. Link the primary source, not a newsletter summarising it.
3. Say why an engineer here should care, in one sentence.
4. No vendor announcements without a technical change behind them.

### Fields

| Field | Notes |
| --- | --- |
| `title` | Sentence case. What changed, not "Announcing…". |
| `kind` | Drives the label and the filters. One of the five above. |
| `date` | When it happened. Editions group by ISO week, Monday to Sunday. |
| `tags` | Must come from the shared vocabulary — see below. |
| `sourceUrl` | The primary source. The displayed label is derived from it. |
| `by` | Your GitHub handle. It becomes the byline. |

---

## `content/dispatch/` — long-form articles

```markdown
---
title: We cut our EKS bill 43% and nobody noticed
kicker: FinOps         # FinOps | Platform | Applied AI | Incident | Careers
dek: A Lagos fintech moved every stateless workload onto Karpenter spot pools
  over six weeks. The savings were real; the interesting part was the guardrails.
author: Chinedu Eze
publishedAt: 2026-09-02
---

Your first paragraph.

Your second paragraph. Blank lines separate paragraphs; a line break inside a
paragraph is just soft wrapping and will be joined together.
```

Reading time is calculated from the body — don't set it.

The `dek` is the standfirst: one sentence that earns the click. It appears on
the feed, so make it work without the headline above it.

---

## `content/events/` — meetups, webinars, workshops

```markdown
---
id: evt_k8s_cost_clinic          # NEVER change this once merged
title: "Kubernetes cost clinic: bring your bill"
city: Lagos                      # Lagos | Abuja | Port Harcourt | Virtual
venue: Zone Tech Park, Gbagada
format: Meetup                   # Meetup | Webinar | Workshop
startsAt: 2026-09-12T17:30:00+01:00
endsAt: 2026-09-12T20:30:00+01:00
capacity: 180
speakers:
  - name: Chinedu Eze
    role: Staff SRE, Kuda
    talk: Reading a Kubernetes bill line by line
agenda:
  - time: 5:30 pm
    item: Doors, jollof, introductions around the room
  - time: 6:00 pm
    item: "Framing: the four places money hides in a cluster"
---

What the event is, in a paragraph or two. This shows on the listing and on the
event page.
```

**`id` is immutable.** RSVPs are stored against it, so changing it orphans
everyone who signed up, and CI fails if a merged id disappears. To rename an
event, change the `title` and the filename but not the `id`.

Dates and times are derived from `startsAt` / `endsAt`, so the date chip, the
long date and the time range all stay consistent. Use a `+01:00` offset (West
Africa Time); virtual events are still scheduled in Lagos time.

`going` is **not** a field. Attendance comes from the database, not from git.

---

## The tag vocabulary

Tags are shared with the Q&A section, which is what makes a Radar entry link
itself to related questions. Only these are accepted:

```
kubernetes  finops  ai  terraform  devops
reliability ci-cd   security  opentofu  observability
```

Adding a tag means adding it to `TAGS` in
`packages/core/src/data/questions.ts`, and is worth a conversation first — an
unbounded vocabulary stops being useful for filtering.

---

## What CI checks

Every pull request runs `pnpm content:validate`, which fails with the file, the
field and what it expected:

```
content/radar/2026-09-04-foo.md: field "kind" —
  expected one of release|deprecation|tool|paper|regional, got "annoucement"
```

It checks that front matter parses, required fields are present, enums are
valid, dates are real, tags are in the vocabulary, source URLs parse, slugs are
unique, and that no event `id` has vanished.

Two maintainers review, and it ships with the next edition.
