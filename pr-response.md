# PR Response Doc — CineLog Watchlist Feature

## AI Usage
<!-- Fill in at the end — how you used AI tools during this project -->

## Comment 1 — Rename

**What I did:**
Renamed `save_to_watchlist()` to `add_to_watchlist()` in the watchlist service to match the project's existing `verb_to_noun` naming convention. I also updated the import and call site in `routes/watchlist.py`.

**How I verified:**
I used a project-wide search for `save_to_watchlist` to confirm no old references remained. I then ran `pytest tests/ -v` to verify that the existing test suite still passed.

## Comment 2 — Deduplication
**What I did:**

**How I verified:**

## Comment 3 — Missing test
**What I did:**

**How I verified:**

## Comment 4 — Default visibility
**My position:**

**Reasoning:**

**Tradeoff acknowledged:**

## Comment 5 — Sort order
**My position:**

**Reasoning:**

**Engagement with reviewer's point:**

## Comment 6 — Rebase
**What conflicted:**

**How I resolved it:**

**How I verified no conflict remains:**

## PR Description
<!-- Written at the end — feature overview, design decisions, manual testing steps -->
