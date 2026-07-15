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
Added an `AlreadyInWatchlistError` exception and a duplicate-entry check inside `add_to_watchlist()`. After confirming that the film exists, the service searches for an existing `WatchlistEntry` with the same `user_id` and `film_id`. If one exists, the service raises the new exception instead of creating another row. I also updated the route to return HTTP 409 for duplicate requests.

**How I verified:**
I compared the implementation with the existing `add_to_collection()` pattern and confirmed that both perform the existence check before the duplicate check. I ran the full test suite with `pytest tests/ -v`.

## Comment 3 — Missing test

**What I did:**
Created `tests/test_watchlist.py` and added `test_add_to_watchlist_nonexistent_film_raises`. The test creates an isolated in-memory database and a sample user, then verifies that passing a nonexistent UUID to `add_to_watchlist()` raises `FilmNotFoundError`.

**How I verified:**
I modeled the fixture and assertion structure after `test_add_to_collection_nonexistent_film_raises` in `tests/test_collection.py`. I ran `pytest tests/test_watchlist.py -v` and then the complete suite with `pytest tests/ -v`.

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
