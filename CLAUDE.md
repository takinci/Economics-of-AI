# CLAUDE.md — Economics-of-AI

## Project in one paragraph
"Who Pays for Radiology AI?": a single-page static website (GitHub Pages, https://takinci.github.io/Economics-of-AI/)
by Tugba Akinci D'Antonoli. It accompanies her RSNA 2026 talk and a paper in preparation: a long-form briefing on
how radiology AI is paid for across 18 "world tour" stops, with a filterable map, framework, recommendations and a
57-item reference list. Readers are radiologists, payers and policymakers. "Correct" means every figure, country
fact and citation matches the slides/paper and its cited source, and the page renders and filters properly.

## Commands
- Install: none (no package manifest; plain HTML/CSS/JS, fonts from Google Fonts)
- Run: open index.html in a browser, or `python3 -m http.server` and visit localhost:8000
- Test: none exist (0 tests). Closest check: extract the inline <script> blocks and run `node --check` on them (passes)
- Build: none locally. GitHub Actions runs Jekyll (actions/jekyll-build-pages) on every push to main, then deploys
- Lint/format: none configured

## Map of the code
- index.html — the whole site: <style> (~lines 12-200), nav/hero/sections, world-map SVG, references, two <script> blocks. No tests.
  - Line ~278 is a ~55k-char SVG map line, line ~420 the ~14k-char reference list, line ~462 the ~11k-char STOPS JSON: large — search, don't read whole
  - STOPS array (script) holds the 18 stops; the per-stop cards, map dots and filters are rendered from it
  - Light/dark theme: CSS tokens on :root, `data-theme` attribute, toggle button + localStorage in the first script
- README.md — description, background, contribute link, author
- LICENSE — all rights reserved; terms are also summarised in the About section
- .github/workflows/jekyll-gh-pages.yml — Pages build + deploy on push to main
- docs/ — LESSONS.md and specs/ for the spec → plan → step workflow

## Project rules
- Content is scientific: do not change figures, country facts, dates or citations unless the user supplies the source. Keep sources shown with each claim.
- Status date ("status November 2026") appears in the hero, About section and README; update all together. "Accessed <month> 2026" dates in references are access dates, not the status date.
- Talks named on the site: RSNA 2026 only (EuSoMII mention was deliberately removed).
- Contribution form link (Google Forms) appears in the nav, About section and README; keep them consistent.
- Style follows the user's RSNA slides: deep purple #4F2670, light-blue rule, blue headings, orange numerals, Carlito headings, Arial body, hexagon pattern. Avoid generic "AI-looking" styling.
- Keep dark and light modes both working (tokens defined for both; test both).
- Layout must work at phone width; no horizontal page scroll (the map scrolls inside its box).
- Payment categories are Yes / Indirect / No / Reported; colours and counts must agree across map, cards, tally bars and keys.
- No build step or dependencies: keep it one self-contained file unless asked.

## Never do without asking (project-specific)
- .github/workflows/ (deploy config) and anything that changes how Pages builds
- git push (a push to main deploys the live site immediately)
- LICENSE text or the copyright/licence wording
- Adding external scripts, trackers or analytics; adding any dependency or build tool
- Editing the reference list or STOPS data content (see rules above)
- Changing the contribution form URL
