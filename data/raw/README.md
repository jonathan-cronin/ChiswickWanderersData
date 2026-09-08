# data/raw

Drop point for raw match footage on this machine.

**Nothing in this folder is tracked by git** (see the `data/raw/*` rule in
`.gitignore`) -- this file is the single exception, so the folder still exists
in a fresh clone. Footage lives here, or on an external drive with this folder
pointing at it; either way it never reaches GitHub.

One folder per match, named with the match ID:

```
data/raw/2026-09-12_<opponent-slug>_H/
    01_first-half.mp4
    02_second-half.mp4
    notes.txt          # optional: rig position, weather, anything odd
```

See `docs/capture.md` for the naming rules.
