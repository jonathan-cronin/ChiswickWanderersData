# Chiswick Wanderers Data

Match data for Chiswick Wanderers: footage capture conventions, structured
match records, and (later) analysis built on top of them.

First match: **Saturday 2026-09-12.**

## Footage is not in this repo

Match video is stored **locally, outside version control**. Raw footage is too
large to push to GitHub, and a clip committed by accident stays in history
until someone rewrites it. `.gitignore` blocks the common video extensions and
the whole of `data/raw/` as a backstop.

This repo tracks code, schemas and small structured data. See
[docs/capture.md](docs/capture.md) for where footage actually lives and how it
is named.

## Layout

```
data/
  raw/        # git-ignored. Match footage lands here, one folder per match.
  matches/    # tracked. Structured per-match data. Schema still to be decided.
docs/
  capture.md  # naming and footage conventions.
```

## Match ID

One ID per match, `YYYY-MM-DD_<opponent-slug>_<H|A>`, used for both the
footage folder and any data files:

```
2026-09-12_brentford-casuals_H
```

Full rules in [docs/capture.md](docs/capture.md).

## Status

Scaffolding only. There is no code here yet -- the intent is that the
conventions are settled *before* the first match, so Saturday's footage has
somewhere obvious to land and nothing has to be renamed retrospectively.

Next, once the pole is up and there is real footage to test against:

- Decide the event-logging schema for `data/matches/`.
- Ingest script: copy a card into the right `data/raw/<match-id>/` folder and
  verify the copy.
- Tests, once there is a real recording to run them on.
