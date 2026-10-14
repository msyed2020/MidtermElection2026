# 2026 Midterm Stances

A static web app that lists the November 3, 2026 general-election nominees and compares their policy stances side by side.

**Run it:** open `index.html` in a browser. It has no build step, no server, and no dependencies.

## Coverage (snapshot: 2026-10-13)

- **Senate:** all 35 races, including the Florida and Ohio specials. 11 have issue-by-issue comparisons.
- **Governor:** all 36 races. 8 have issue-by-issue comparisons.
- **House:** 32 competitive districts, all with comparisons. This is not all 435 seats.

## Views

- **Races:** filter by office, state, competitiveness or name, then compare a race's candidates issue by issue. You can hide issues or show only the issues where their labels differ.
- **By issue:** one issue across every race, with label counts by party.
- **Compare:** up to 4 candidates from any races, side by side.

## Data

- `data/races.js`: the roster (nominees, incumbency and ratings). Nominees come from Wikipedia's 2026 election articles and were cross-checked against news coverage. Ratings are from Cook and Sabato as listed there.
- `data/guides/*.js`: per-race stances, one file per race. Each is a paraphrase of the matching [guides.vote](https://guides.vote) voter guide, whose URL is the second argument to `G(...)`. The labels ("Ban", "Tighten", etc.) are guides.vote's own.

### Adding a race guide

1. Create `data/guides/<race-id>.js` containing `G("<race-id>", "<source url>", { candidates: [...], issues: [{ issue, positions: { "<Name>": { label, detail } } }] })`.
2. Make the candidate names match `data/races.js` exactly.
3. Add a `<script>` tag for the file in `index.html`.

Use issue names from `ISSUES` in `app.js`. Other names still display, but they sort last and have no explanatory question.

## Caveats

The stance text is condensed from the source guides with AI assistance, so check the linked guide before relying on a specific claim. "No position found" means the source found no stated position.
