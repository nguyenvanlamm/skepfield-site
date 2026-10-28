# UX / AX Review: Skepfield landing site

Target: https://nguyenvanlamm.github.io/skepfield-site/ · orchestrated-by: design-optimizer · 2026-10-28

## Executive Summary

**Outcome: PASS.** All 11 aspects in scope have a supported status (clarity was skipped and belongs to dont-make-me-think), and the validator exits 0. This audit found **5 findings** (0 critical, 0 high, 2 medium, 3 low) and set **6 plan tasks**. PASS describes how complete the audit was. It is not a grade for the product.

Strengths, all with evidence:
- Fast, light, script-free pages. In 8 of 9 lab runs LCP was 0.7–1.6 s, CLS stayed at or below 0.026 and pages weighed 97–226 KB (E6).
- The approved look is consistent across all three pages and holds from 320 to 1440 px with no horizontal overflow (E2, E10).
- The AI/search basics are in good order: the host-root robots.txt lists the project sitemap, the sitemap is truthful, JSON-LD parses and matches the page, llms.txt is accurate and every content line is in the initial HTML (E11–E14, E16).

Top priorities:
1. **T2 (P2, F1):** self-host the fonts and add a "This website" section to the privacy policy. As shipped, every page calls Google Fonts, but the copy says "No tracking" and "collects nothing about you".
2. **T5 (P2, F4):** give interested visitors one next step under the inert "Coming soon to the App Store" pill. A launch-day email line would do it, with no store link or price.
3. **T3 (P3, F2):** a one-line CSS fix for the focus ring on the dark privacy panel, which measures 2.03:1.

## Scope and Evidence

- **Mode:** evidence-only, using the orchestrator bundle captured at 2026-10-28T14:10:00Z. On top of that I ran a separate live-web lab pass with Playwright and system Chrome 154 (recorded in `lab-measure.json` as 2026-10-28T13:54:35Z by the machine clock), plus one read-only `curl` HEAD each on llms.txt and a `.reports/` path. Orchestrated by **design-optimizer**.
- **Audience and goal:** iPhone players who like calm logic puzzles, plus search engines and AI assistants. The goal is to understand the game and see that it is not released yet: no App Store link, badge or price.
- **Sample:** index.html (the entry page and main task), support.html and privacy.html. 404.html was read for context only.
- **Exclusions:** the host-root repo nguyenvanlamm.github.io (read, but not editable here), the app itself, and the other projects under the same host.
- **Skipped:** `clarity` (owned by dont-make-me-think). No unknown skip ids were given.
- **Reviewer path:** inline. This run is already a delegated member of design-optimizer, so no nested workers were spawned.
- **Repo sync:** not performed. The output directory is inside the worktree, but the checkout is read-only for this run, and the manifest says it was fast-forwarded to origin/main 100ab67, which is the live version. I took a baseline hash of 36 files before inspection (excluding this output directory) and compared against it at the end.
- **Tool limits:** no screen reader, no real iPhone, no field data (CrUX/analytics), no crawler logs. The agent-readiness scan was normalised to the origin, so it counts only as corroboration.

| ID | Source | Method | Observation (short) |
|---|---|---|---|
| E1 | evidence/manifest.json, page.html, head.json | orchestrator capture | 200; full content is in the initial HTML; robots index,follow; canonical is correct |
| E2 | evidence/screenshots/desktop.png, mobile.png, mobile-fold.png | headless Chrome | approved look renders; hero and pill above the fold at 390×844; the blank band under the desktop footer comes from the capture window (4200 px vs a 3758 px document) |
| E3 | index.html:67-69, 87, 166-169, 211, 213, 288, 303 | source | Google Fonts link; straw focus ring; dark `.calm` panel; `<p class="soon">` is static text |
| E4 | support.html:30-32, 53, 69, 72-77 | source | Google Fonts; `li::marker` in straw; personal support email |
| E5 | privacy.html:68-95 | source | the policy covers the game only, not the website or support emails |
| E6 | lab-measure.json metrics | Playwright, 3 pages × 320/390/1440 | LCP 0.7–1.6 s (one outlier at 3.55 s caused by a 3.3 s TTFB); CLS ≤0.026; no overflow |
| E7 | lab-measure.json requests | Playwright | every page loads fonts.googleapis.com and fonts.gstatic.com (72–139 KB of woff2) |
| E8 | lab-measure.json focus, shots/index-focus-first.png | keyboard Tab ×12 | tab order is logical and every link has a 3px outline; the pill never receives focus |
| E9 | contrast.py, shots/index-calm-focus-d1440.png | WCAG luminance | focus ring on the hedgerow panel is 2.03:1; straw markers on card are 3.97:1; text pairs pass AA |
| E10 | shots/index-m320-*.png, index-768-fold.png, support-/privacy-m390-full.png | screenshots | clean wrapping at 320 and 768 |
| E11 | evidence/robots.txt (host root) | capture | allow all; Content-Signal; Skepfield sitemap at line 20 |
| E12 | evidence/site-sitemap.xml | capture | 3 canonical URLs; lastmod matches Last-Modified |
| E13 | evidence/site-llms.txt, llms.txt; live HEAD 200 text/plain | capture + curl | well-formed and accurate; linked from the host root |
| E14 | JSON-LD blocks in all 3 pages | JSON parse + copy comparison | parses; no invented offers or ratings |
| E15 | evidence/agent-readiness/scan.json | origin-normalised scan | robots, sitemap, AI rules and content signals pass; markdownNegotiation and linkHeaders fail |
| E16 | lab-measure.json headers | response headers | max-age=600; no X-Robots-Tag; no Link header; no challenge |
| E17 | live HEAD on a .reports/ path → 404; git ls-files | curl + git | tracked `.reports/` is not published, because Jekyll skips dot-folders |

## Human UX

| Aspect | Status | Rationale | Evidence / findings |
|---|---|---|---|
| clarity | not-tested | skipped — owned by dont-make-me-think | — |
| brand | pass | Same tokens, Alegreya pair, beehive mark and calm tone on all three pages, matching the approved look. Strategic fit beyond the approved mockup was not assessed. | E2, E3, E4, E5, E10 |
| responsive | pass | No horizontal overflow at 320, 390, 768 or 1440; hero, chips, rule cards and season lists wrap cleanly. Not tested: landscape, text-spacing overrides, real devices. | E2, E6, E10 |
| accessibility | issues | Pass: lang, labelled landmarks, h1→h2→h3 order, descriptive alt, aria-hidden decoration, logical tab order, visible focus. Issues: the focus ring on the dark panel and the support list numbers. Not tested: screen reader. | E3, E4, E8, E9 · F2, F3 |
| performance | pass | Lab only: LCP 0.7–1.6 s in 8 of 9 runs, CLS ≤0.026, no JS, 97–226 KB. No field CWV exists yet. | E6, E7, E16 |
| conversion | issues | The copy makes the value clear, but the "coming soon" end point offers no action, and the trust promise does not cover the website itself. | E3, E5, E7, E8 · F1, F4 |

No human understanding test was run, so human comprehension is unconfirmed (clarity is owned elsewhere).

## AI/Search AX

| Aspect | Status | Rationale | Evidence / findings |
|---|---|---|---|
| robots-sitemap | pass | The host-root robots.txt (the only one crawlers read) allows all and lists the project sitemap. The sitemap holds 3 canonical URLs with truthful lastmod. The 404 page is noindex. The project-path robots.txt only documents policy and is harmless. | E1, E11, E12, E15 |
| structured-data | pass | WebSite plus VideoGame/MobileApplication, with ContactPage and WebPage linked by stable @ids, all agreeing with the visible copy. Leaving out offers and ratings is correct while the game is unreleased. Schema validity is not the same as rich-result eligibility. | E14 |
| markdown-pages | issues | There is no Markdown representation. GitHub Pages cannot negotiate `Accept: text/markdown`, and Jekyll renders .md files to HTML. This is an optional format: low severity, and llms.txt already carries the facts. | E13, E15, E17 · F5 |
| llms-txt | pass | Follows the llms.txt proposal format, the facts are accurate, the links are valid, and it is served as text/plain and linked from the host root. llms.txt is a proposal; this audit does not claim any provider reads it. | E13 |
| crawler-access | pass | The owner's policy (all bots, including AI training) is documented and respected. All content is in the initial HTML, with no X-Robots-Tag, auth or WAF. Access by verified crawlers was not tested because GitHub Pages provides no logs. | E1, E11, E15, E16 |
| ai-actions | pass | Scoped to canonical share links: each page's canonical and og:url match the sitemap, and a 1200×630 share card exists. There are no copy, share or open-in-AI controls, and I am not recommending any for a no-JS coming-soon page. | E1, E3, E12 |

The origin-level agent-discovery checks in scan.json (/.well-known agent cards, API catalog, OAuth, MCP, DNS-AID, Link headers) apply to the host-root repo and need response headers that GitHub Pages cannot set. They belong to website-agent-readiness and are not repeated here.

## Prioritized Findings

| ID | Aspect | Kind | Severity / confidence | Look | Evidence |
|---|---|---|---|---|---|
| F1 | conversion | observed | medium / high | look-preserving | E3, E4, E5, E7 |
| F4 | conversion | observed | medium / medium | look-preserving (pill restyle = owner proposal) | E2, E3, E8 |
| F2 | accessibility | observed | low / high | look-preserving | E3, E8, E9 |
| F3 | accessibility | observed | low / high | changes the look (owner proposal) | E4, E9, E10 |
| F5 | markdown-pages | observed | low / high | look-preserving | E13, E15, E17 |

**F1: the site says "No tracking" but every page calls Google Fonts, and the privacy policy does not cover the website.** index.html:213 and :288 say "No tracking" and "collects nothing about you". Meanwhile index.html:67-69, support.html:30-32 and privacy.html:30-32 load fonts.googleapis.com and fonts.gstatic.com on every visit (E7). privacy.html:68-95 covers only the game: it says nothing about hosting logs, the font requests, or emails sent to support. This review does not assess legality.
*Fix (look-preserving):*
1. Download the OFL woff2 files for the exact faces in use (Alegreya 800, plus 700 and italic 500 if kept; Alegreya Sans 400/500/700/800) into `assets/fonts/`.
2. Add `@font-face { font-family: "Alegreya Sans"; src: url(assets/fonts/alegreya-sans-400.woff2) format("woff2"); font-weight: 400; font-display: swap; }` and the equivalent rule for each face.
3. Delete the two `preconnect` lines and the Google stylesheet on all four pages (404.html uses absolute `/skepfield-site/assets/fonts/...` URLs).
4. Add to privacy.html before "Changes":
   `<h2>This website</h2><p>This site is a set of static pages hosted on GitHub Pages. It sets no cookies and runs no scripts, ads or analytics. Like any web host, GitHub may log technical data such as your IP address to deliver and protect the site. If you email us, we use your address and message only to reply.</p>` (the owner confirms the wording).

**F4: "Coming soon to the App Store" looks like the main button but does nothing, and the page offers no next step.** The pill at index.html:211 and :303 is a `<p>` with the beeswax fill, straw ring and lift shadow that the design uses for emphasis (E2). It never receives focus (E8), and nothing lets a visitor hear about the launch. The observed part is that no action exists. Whether visitors actually try to tap the pill is a hypothesis.
*Fix (look-preserving):* after index.html:211 add `<p class="launch-note">Want a note on launch day? <a href="mailto:lamnv260398@gmail.com?subject=Skepfield%20launch">Email us</a> and we will write once when it is out.</p>` and `.launch-note { margin-top: 12px; color: var(--ink-2); }`. It adds no store link, badge or price, and the owner must agree to send that one email. *Owner proposal (changes the look), only if a hallway test shows people tapping the pill:* remove the pill's `var(--lift)` shadow so it reads as a status badge.

**F2: the focus ring is hard to see on the dark privacy panel.** The ring is straw #A8721F against hedgerow #2F5636, which is 2.03:1 and below the 3:1 required by WCAG 2.2 SC 1.4.11 (index.html:87 and :166-169; screenshot `shots/index-calm-focus-d1440.png`).
*Fix (look-preserving):* after index.html:169 add `.calm a:focus-visible { outline-color: var(--wax); }`. Beeswax on hedgerow is 4.60:1.

**F3: the support list numbers are below text contrast.** support.html:53 sets `li::marker { color: var(--straw); font-weight: 800; }`, which puts the "How to play" numbers at 3.97:1 on the card, below the 4.5:1 required by SC 1.4.3 (`shots/support-m390-full.png`).
*Owner proposal (changes the look):* use `color: #8A5D17` (5.52:1) or `var(--soil)` (8.09:1). The bullets in privacy.html are non-text discs and can stay as they are.

**F5: there is no Markdown version, and the host cannot negotiate one.** scan.json reports markdownNegotiation as failing. GitHub Pages cannot vary the response by `Accept` header. llms.txt (200 text/plain) already carries every public fact.
*Fix (look-preserving):* the default is to accept this as a platform limit and change nothing. If the owner wants .md twins anyway:
1. First move the tracked `.reports/` folder off `main`. `.nojekyll` would publish dot-folders, and today they are hidden only because Jekyll skips them (E17).
2. Add `.nojekyll`, plus `index.md`, `support.md` and `privacy.md`.
3. Add `<link rel="alternate" type="text/markdown" href="index.md">` to each page and list the .md files in llms.txt.

Already reported by search-optimizer, so not repeated here: the rules section comparing stones to a named third-party game (S-09, owner decision) and the host-root robots and llms lines (now present, E11 and E13).

## Improvement Plan

| ID | Phase | Priority | Findings | Task | Owner | Effort | Depends on | Expected impact | Acceptance checks |
|---|---|---|---|---|---|---|---|---|---|
| T1 | 0 | P2 | — (measurement) | Manual VoiceOver and real-iPhone pass over the three pages | QA/accessibility | S | — | Closes the screen-reader and device gaps | VoiceOver reads each page in logical order with no unlabeled or duplicated items; device, iOS version and date recorded |
| T2 | 1 | P2 | F1 | Self-host fonts and add "This website" to privacy.html | frontend + owner | M | — | No-tracking promise holds for the website; two third-party origins removed | Cold load of index, support, privacy and 404 shows 0 requests to Google font hosts; 390 and 1440 screenshots show the same faces and weights; privacy.html covers hosting logs and support emails |
| T3 | 1 | P3 | F2 | Beeswax focus ring inside `.calm` | frontend | XS | — | Focus is visible on the dark panel | Tab to "privacy policy" shows a #EDB841 ring at ≥3:1 against #2F5636; rings elsewhere unchanged |
| T4 | 1 | P3 | F3 | Owner decision: darker support list numbers | owner/design | XS | — | AA-readable numbers | Decision recorded; if approved, marker colour ≥4.5:1 on #FAFBF6 |
| T5 | 2 | P2 | F4 | Launch-day email line under the pill | content + owner | S | T2 | Interested visitors get one optional next step (no uplift claimed) | Link reachable by keyboard and opens a mail draft with the subject set; still no App Store link, badge or price; the T2 privacy text ships first; 5-person hallway test confirms people know what it is, that it is not out yet, and how to hear when it is |
| T6 | 3 | P3 | F5 | Owner decision on Markdown twins (default: llms.txt only) | owner | XS | — | Optional AX format decided on the record | Decision in README.md; if twins are added, `.reports/` is off main and its URLs return 404, and each .md returns 200 with copy matching its HTML |

Ordering follows phase, then priority. T5 (phase 2) depends on T2 (phase 1) so that the privacy policy explains how emails are used before the page invites them.

## Limitations and Next Step

- **Evidence gaps:**
  - All performance figures are lab measurements from one machine and network; there is no field CWV yet.
  - No screen-reader or real-device test (plan task T1).
  - Verified-crawler access is not observable on GitHub Pages.
  - The agent-readiness scan covered the origin, not the project path.
  - The legal adequacy of the privacy text was not assessed.
- **No certification:** this is not a WCAG certification and not a forecast of indexing, AI citation or conversion. The validator checks structure only.
- **Target state:** none of the 36 baseline-hashed files changed and no site file changed. Four new files appeared during the run in sibling member folders (`reports/dont-make-me-think/` and `reports/viral-product-evaluator/`). Other design-optimizer members wrote them in parallel; this run did not.
- **Artifacts:**
  - `/home/lam/Documents/projects/skepfield-site/.claude/worktrees/s9-site/.reports/design-optimizer/reports/ux-ax-review/UX_AX_REVIEW.md`
  - `/home/lam/Documents/projects/skepfield-site/.claude/worktrees/s9-site/.reports/design-optimizer/reports/ux-ax-review/ux-ax-findings.json`
  - Lab data: `lab-measure.json`
  - Extra screenshots: `shots/`

Would you like me to implement any of these fixes? Choose the finding/task IDs and scope.
