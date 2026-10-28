## SEO & AI Bot Audit Report

orchestrated-by: search-optimizer
**Project:** skepfield-site (worktree `s9-site`, branch `worktree-s9-site`)
**Framework:** generic static HTML (GitHub Pages, branch `main`, root; Jekyll build, no `.nojekyll`)
**Live URL:** https://nguyenvanlamm.github.io/skepfield-site/ (project path on the user site; served page is byte-identical to the committed `index.html`)
**Files audited:** 3 / 3 before, 4 / 4 after (404.html added)
**Date:** 2026-10-28
**skip-checks:** `agent-readiness-scan` (skipped, owned by design-optimizer, which runs the approved isitagentready.com scan next)

### Before (audit_seo.py, committed 22ce958)

0 critical · 8 warning · 4 info

#### Warnings
1. [index.html:7] Meta description 221 chars (recommended 140-160).
2. [index.html] No JSON-LD structured data.
3. [privacy.html] No JSON-LD structured data.
4. [privacy.html] No Open Graph tags.
5. [support.html] No JSON-LD structured data.
6. [support.html] No Open Graph tags.
7. [project] No robots.txt in the site (the host-root robots.txt exists and allows all; see below).
8. [project] No sitemap.xml (live https://nguyenvanlamm.github.io/sitemap.xml is 404 and the root robots.txt lists no Skepfield sitemap).

#### Info
1. [privacy.html] No Twitter Card tags.
2. [support.html] No Twitter Card tags.
3. [project] No llms.txt (live /skepfield-site/llms.txt is 404; the root llms.txt has no Skepfield entry).
4. [project] No /.well-known/ai-plugin.json (deprecated; not applicable to a game landing page).

#### Manual review
- [index.html:18-22] og:image is a 390×844 portrait screenshot with `twitter:card=summary`: large previews crop it badly. Needs a 1200×630 card.
- Title, headings (one h1 per page, h2/h3 in order), image alt texts, width/height on images, canonical, lang, viewport: all fine.
- Content matches `skepfield/store/listing-en-US.md` (rules, 4 × 40 fields, sizes, daily 8×8, Almanac 3/day, tools 3+2, cap 9, Kit 10+5).
- Body copy of index.html (rules section) says stones work "like the numbers in Minesweeper". Not changed (approved copy), flagged for the owner since the pipeline avoids naming other games.

### Project-level findings
- robots.txt: crawlers read only https://nguyenvanlamm.github.io/robots.txt (repo `nguyenvanlamm.github.io`). It allows all bots (`User-agent: *`, `Allow: /`, Content-Signal search/ai-input/ai-train = yes) but has no `Sitemap:` line for skepfield-site.
- sitemap.xml: absent.
- llms.txt: absent here and not listed in the root llms.txt.
- Structured data: none.
- AI bot directives: allowed at the host root (no change needed there except the Sitemap line).

### Research (Step 3)
- Google: a VideoGame-only SoftwareApplication markup gets no rich result; co-type it, e.g. `["VideoGame", "MobileApplication"]` (developers.google.com/search/docs/appearance/structured-data/software-app). The rich result also needs offers and a rating, which a pre-release game cannot honestly give, so no rich result is expected; the markup still helps entity understanding and AI answers.
- Third-party reports (unverified) say FAQ rich results were retired in 2026; no FAQPage markup was added anyway (no visible FAQ on the site).

## Improvement Plan (Step 5)

Approval: pre-authorized by the pipeline for S9 site fixes (owner away; caller instruction 2026-10-28). Constraint: keep the approved look, no restyling, no App Store link, no prices, no other games named.

### Priority 2: Warnings
- [x] Shorten the home meta description to 158 chars -- index.html
- [x] Open Graph + Twitter tags on privacy and support -- privacy.html, support.html
- [x] JSON-LD: WebSite + VideoGame/MobileApplication (operatingSystem iOS, no offers, no rating) -- index.html; WebPage -- privacy.html; ContactPage -- support.html
- [x] sitemap.xml with the three pages -- sitemap.xml
- [x] robots.txt copy documenting the policy (only the host-root one counts) -- robots.txt

### Priority 3: Enhancements
- [x] 1200×630 share card in the approved palette and fonts (hero headline + real game screenshot); og:image/twitter:image on all pages, `summary_large_image` -- assets/share-card.jpg
- [x] og:locale, twitter:title/description/image/alt, robots max-image-preview:large -- index.html
- [x] llms.txt with game facts from the pages and the store listing -- llms.txt
- [x] 404.html (noindex, absolute /skepfield-site/ links, same styles as support) -- 404.html
- [ ] llms-full.txt -- skipped: three short pages, llms.txt already carries every fact; Markdown page copies belong to the agent-readiness `markdown-pages` check (design-optimizer)
- [ ] ai-plugin.json -- skipped: deprecated, no API

## Validation (Step 7)

audit_seo.py after: 0 critical · 3 warning · 2 info. All three remaining warnings and one info are on 404.html (no canonical, no OG, no JSON-LD), which is intentional for a noindex error page served at any wrong URL; the other info is the deprecated ai-plugin.json. index.html, privacy.html and support.html: 0 issues.
Extra checks (python): every JSON-LD block parses; sitemap.xml parses (3 URLs); no image without alt; one h1 per page; no other-game or publisher name and no price in any new or edited head, llms.txt or robots.txt.

## Step 8: Agent-readiness handoff

SKIPPED: `agent-readiness-scan` was passed in skip-checks; the scan (approved at G4, 2026-10-28) belongs to design-optimizer, which runs after this run and after these changes are deployed.

Result: COMPLETE. 0 critical before and after; warnings 8 → 0 on indexable pages (3 intentional on 404.html).
Evidence: audit_seo.py before/after (this report); files changed: index.html, privacy.html, support.html, README.md; added sitemap.xml, robots.txt, llms.txt, 404.html, assets/share-card.jpg.
Uncertainty: not verified live (no push); rich results not expected without offers/rating; root robots.txt and llms.txt need the caller's update.
Decision: No approval needed. Caller: add the Sitemap line and llms entry in nguyenvanlamm.github.io, deploy, then design-optimizer scans.
