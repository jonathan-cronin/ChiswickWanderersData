# Capture conventions

How match footage is named, where it lives, and what to do on matchday.

## Where footage lives

Footage is stored **locally, outside version control**. Raw video is far too
large to push to GitHub, and anything committed by accident stays in history
until the history is rewritten. The repo tracks code, schemas and small
structured data only.

The drop point is `data/raw/` (git-ignored). If disk space is tight, point that
folder at an external drive -- on Windows, from an elevated prompt:

```bash
mklink /D data\raw D:\ChiswickWanderers\raw
```

Back up the drive separately. Losing the repo costs an afternoon; losing the
footage costs the season.

## Match ID

Every match gets one ID, used for its footage folder and any data files:

```
YYYY-MM-DD_<opponent-slug>_<H|A>
```

- `YYYY-MM-DD` -- date of kickoff, not the date you ingest the video.
- `<opponent-slug>` -- opponent in lowercase, hyphenated, no punctuation
  (`Brentford Casuals FC` becomes `brentford-casuals`). Keep the spelling
  identical between matches so the same opponent always sorts together.
- `<H|A>` -- home or away.

Example: `2026-09-12_brentford-casuals_H`

Sortable, unambiguous, and safe as a filename on every platform.

## Footage layout

```
data/raw/2026-09-12_brentford-casuals_H/
    01_first-half.mp4
    02_second-half.mp4
    notes.txt
```

Numeric prefixes keep the halves in order. If the camera splits a long
recording across several files, keep the numbering running (`01_`, `02_`,
`03_`) rather than restarting per half, and record which file each half starts
in inside `notes.txt`.


## Still to decide

Deferred until there is real footage to test against:

- Event-logging schema and where logged data lands in `data/matches/`.
- Whether to keep a compressed proxy of each match alongside the original.
- Retention: how many seasons of raw footage to hold before archiving.
