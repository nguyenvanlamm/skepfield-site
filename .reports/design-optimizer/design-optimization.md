# Design Optimization: https://nguyenvanlamm.github.io/skepfield-site/

Run: design-optimizer · 2026-10-28T14:06Z · mode: audit, then apply (pre-authorized by the pipeline for S9 site fixes; the human was away)
Evidence: evidence/manifest.json · AX ownership case: C (scan approved and returned, but isitagentready.com normalised the target to the origin `https://nguyenvanlamm.github.io`, so it does not name the project URL; scan cited as corroboration)
Members: dont-make-me-think √ (COMPLETE, thinking cost MODERATE) · ux-ax-review √ (PASS) · website-agent-readiness √ (score 2/5, Bot-Aware; plan written, issues not filed by the caller's instruction) · viral-product-evaluator √ (PASS, 55/100)

## Summary
- Thinking cost (dont-make-me-think): MODERATE (lens scores 6-9 of 10; weakest: Affordances 6)
- Agent-readiness score: 2/5 "Bot-Aware" (scanned once, 2026-10-28T13:51:05Z): 4 pass · 13 fail · 6 neutral; next level 3 "Agent-Readable" needs `Accept: text/markdown` negotiation, which GitHub Pages cannot do
- Virality score: 55/100 (Needs work); 6 of 7 FAILs come from fixed product decisions (unreleased, no store link, no players yet, no other game may be named)
- Meta tags: PASS (viral-product-evaluator verified title, description, canonical, full Open Graph and Twitter large card, 1200×630 share card)
- Findings: 0 P0 · 4 P1 · 7 P2 · 13 P3 (5 cross-member duplicates merged)
- Applied: 12 member fixes (index.html, support.html, privacy.html, 404.html, assets/fonts/); 11 items left as owner proposals; 2 not changeable on this host

## Findings

| ID | Pri | Check | Finding | Evidence | Owner | Also reported by | Fix route / status |
|---|---|---|---|---|---|---|---|
| D-01 | P1 | clarity | The only explanation of how a stone counts compared it to another game's numbers; the eight-cell rule (corners included) was never stated | index.html:249 (before) | dont-make-me-think (U2) | search-optimizer S-09 (earlier run) | Fixed, Redesign Mode: "A stone holds no hive. Its number counts the hives in the eight cells around it, corners included, and settles questions the other rules leave open." |
| D-02 | P1 | conversion | "Coming soon to the App Store" is a `<p>` styled like the main button (beeswax fill, ring, shadow) but does nothing, and leaves interested visitors no next step | index.html:106-110, :211, :303; mobile-fold.png | ux-ax-review (F4) | dont-make-me-think (U3, affordance), viral-product-evaluator (V-03, #28) | Partly fixed: next steps added next to it (D-05 jump link, D-07 support link). Owner proposals: drop the pill's button cues; a launch-day mailto line; link both pills to the App Store on launch day |
| D-03 | P1 | virality | Hero sub has no number or daily hook ("160 fields" never appears) | index.html:210 | viral-product-evaluator (V-01) | — | Owner proposal (approved hero copy): "One to five quiet minutes of pure logic: a new 8×8 field every day, and 160 more across four seasons. One straw hive per plot; numbered stones count the hives around them." |
| D-04 | P1 | virality | The daily field's solved card has no share action (no share loop) | game repo lib/ui/field_cards.dart:72-152 | viral-product-evaluator (V-02) | — | Owner proposal, game app (out of scope): spoiler-free "Share" for Today's field via Clipboard |
| D-05 | P2 | clarity | No shortcut to "what is free and what is paid"; #seasons is far down on a phone | index.html:202, :212-214; mobile.png | dont-make-me-think (U4) | viral-product-evaluator (V-08, #16) | Fixed, Redesign Mode: "What's free and what's paid" link to #seasons under the hero chips. A "Seasons" nav item would wrap at 390 px: owner proposal |
| D-06 | P2 | conversion | Copy says "No tracking", but every page called fonts.googleapis.com / fonts.gstatic.com on each visit; privacy.html covers only the app, not the website | index.html:67-69; support/privacy/404 head; ux-ax lab-measure.json | ux-ax-review (F1) | — | Fixed, frontend-design: Alegreya 800 + Alegreya Sans 400/500/700/800 self-hosted (latin woff2, OFL texts included), Google Fonts links removed from all four pages, two preloads on index. Owner proposal: a "This website" paragraph in privacy.html (legal wording, owner confirms) |
| D-07 | P2 | clarity | Smokers and Spare Bees named in the Free card before they are explained; 38-word item | index.html:265, :275 | dont-make-me-think (U1) | — | Fixed, Redesign Mode: defined in Starter tools; Kit item shortened to "10 Smokers and 5 Spare Bees. Buy it as often as you need." Reward facts unchanged |
| D-08 | P2 | virality | Nothing names what puzzle players dislike (energy, timers) | index.html:290-293; listing-en-US.md:72 | viral-product-evaluator (V-04) | — | Fixed, frontend-design: list item "No energy, no timers to wait out, no daily limit on play." (listing wording) |
| D-09 | P2 | virality | The name "skep" is never explained; end block has no quotable line | index.html:302 | viral-product-evaluator (V-05) | — | Fixed, frontend-design: end lede "A skep is a traditional straw beehive. Set the first one and see where the field leads." |
| D-10 | P2 | virality | Faceless footer, no maker named | index.html:309 | viral-product-evaluator (V-06) | — | Owner proposal (owner confirms name and wording) |
| D-11 | P2 | accessibility | Measurement gap: no VoiceOver or real-iPhone pass | UX_AX_REVIEW.md T1 | ux-ax-review (T1) | — | Owner task (manual check) |
| D-12 | P3 | clarity | "plot" never defined | index.html:244 | dont-make-me-think (U5) | — | Fixed, Redesign Mode: "Every plot (one coloured patch of the field) gets exactly one hive." |
| D-13 | P3 | clarity | End block is a dead end (brand + an inert pill) | index.html:299-304 | dont-make-me-think (U9) | — | Fixed, Redesign Mode: "Questions before launch? Visit support" under the pill |
| D-14 | P3 | clarity | Footer links about 27 px tall on phones | index.html:181; support/privacy/404 footers | dont-make-me-think (U10) | — | Fixed: `padding: 10px 0; margin: -10px 0` (taller tap target, same layout); index/support in Redesign Mode, privacy/404 in the frontend-design pass |
| D-15 | P3 | clarity | Support "How to play" is one 7-sentence paragraph | support.html:78 | dont-make-me-think (U11) | — | Fixed, Redesign Mode: 6-item list, wording unchanged |
| D-16 | P3 | accessibility | Focus ring on the "privacy policy" link inside the dark panel: straw on hedgerow 2.03:1 (SC 1.4.11 needs 3:1) | index.html:87, :166-169 | ux-ax-review (F2) | — | Fixed, frontend-design: `.calm a:focus-visible { outline-color: var(--wax) }` = 4.60:1 |
| D-17 | P3 | accessibility | Support rule numbers (ol markers) straw on card 3.97:1 (SC 1.4.3 needs 4.5:1) | support.html:53, :72-77 | ux-ax-review (F3) | — | Fixed, frontend-design: `ol li::marker { color: #8A5D17 }` (deeper straw, 5.52:1); bullets keep straw (graphical, 3:1 met) |
| D-18 | P3 | clarity | Trust chips are white pills with the button shadow, so they look tappable | index.html:113, :212-214 | dont-make-me-think (U6) | — | Owner proposal (restyle) |
| D-19 | P3 | clarity | "How it plays" comes before "The rules" | index.html:221-251 | dont-make-me-think (U7) | — | Owner proposal (layout) |
| D-20 | P3 | clarity | No price cue in "Buy once" (no price can be shown before release) | index.html:277 | dont-make-me-think (U8) | — | Owner proposal: "Prices will show in the App Store at launch." |
| D-21 | P3 | virality | No player voice (unreleased) | index.html | viral-product-evaluator (V-07) | — | Owner proposal: quotes from TestFlight testers, new section |
| D-22 | P3 | virality | Nothing playable on the page | index.html:217, :227 | viral-product-evaluator (V-09) | — | Owner proposal: embed one fixed Spring field (needs a web build, new section) |
| D-23 | P3 | markdown-pages | No Markdown versions of the pages; `Accept: text/markdown` returns HTML | live curl; scan.json markdownNegotiation fail | ux-ax-review (F5) | website-agent-readiness scan | Not changed: GitHub Pages cannot negotiate; llms.txt already carries every fact. `.md` twins would need `.nojekyll`, which would also publish `.reports/` |
| D-24 | P3 | agent-readiness-scan | 2/5 Bot-Aware; failing: markdownNegotiation, linkHeaders, dnsAid, apiCatalog, oauthDiscovery, oauthProtectedResource, authMd, mcpServerCard, a2aAgentCard, agentSkills, webMcp, ard, personalAgentProtocol | evidence/agent-readiness/scan.json; reports/website-agent-readiness/agent-ready-plan.md | website-agent-readiness | — | Not changed. Not possible on GitHub Pages: Link headers, content negotiation, DNS on github.io. Not applicable to a static marketing site with no API, auth or agent: the 10 discovery checks. `/.well-known/` files would live in the host-root repo anyway. Issues not filed (caller) |

## Check coverage

| Check | Owner | Status |
|---|---|---|
| clarity | dont-make-me-think | issues: D-01, D-05, D-07, D-12 to D-15 fixed; D-18 to D-20 proposals |
| brand | ux-ax-review | pass (same palette, fonts, mark and tone on all pages) |
| responsive | ux-ax-review | pass (no overflow at 320/390/768/1440; re-checked after apply at 375/768/1280) |
| accessibility | ux-ax-review | issues: D-16, D-17 fixed; D-11 manual check |
| performance | ux-ax-review | pass, lab only (LCP 0.7-1.6 s in 8 of 9 runs, CLS ≤ 0.026, no JS) |
| conversion | ux-ax-review | issues: D-02 partly fixed, D-06 fixed (privacy paragraph proposed) |
| robots-sitemap | ux-ax-review (case C) | pass; scan robotsTxt and sitemap pass (origin) |
| markdown-pages | ux-ax-review (case C) | issue D-23, platform limit |
| crawler-access | ux-ax-review (case C) | pass; scan robotsTxtAiRules and contentSignals pass (origin) |
| structured-data | ux-ax-review | pass (JSON-LD parses, stable @ids, no offers or price) |
| llms-txt | ux-ax-review | pass (200 text/plain, accurate, listed in the host-root llms.txt) |
| ai-actions | ux-ax-review | pass (no in-page actions needed; canonical share links and share card) |
| agent-readiness-scan | website-agent-readiness | 2/5, D-24 |
| virality | viral-product-evaluator | 55/100: D-08, D-09 fixed; D-03, D-04, D-10, D-21, D-22 proposals |
| meta-tags | viral-product-evaluator | pass (optional only: og:image:type absent on privacy/support) |

## Skipped (owned elsewhere)
| Check | Skipped by | Owner |
|---|---|---|
| clarity | ux-ax-review | dont-make-me-think |

## Not covered
| Check | Reason |
|---|---|
| — | Every canonical check had an owner. Screen reader, real devices and field data were not tested (lab only) |

## Apply log
- Redesign Mode (dont-make-me-think): D-01, D-05, D-07, D-12, D-13, D-14 (index, support), D-15. Before/after shots: reports/dont-make-me-think/apply/ (local only).
- frontend-design: D-06 (fonts), D-08, D-09, D-14 (privacy, 404), D-16, D-17. README updated for the self-hosted fonts. Shots: apply-shots/ (local only). Contrast: lowest new text pair 5.52:1; focus ring 4.60:1.
- Not applied: every proposal above; no App Store link, badge or price added; "Coming soon to the App Store" kept; no other game named.

## Member reports
- reports/dont-make-me-think/usability-review.md
- reports/ux-ax-review/UX_AX_REVIEW.md, ux-ax-findings.json (validator exit 0), lab-measure.json
- reports/website-agent-readiness/agent-ready-plan.md (13 tasks; scratch scan in .agent-ready/ is not committed); scan copy in evidence/agent-readiness/
- reports/viral-product-evaluator/viral-evaluation.md, verdicts.json
- PNG screenshots are kept on disk only (`.gitignore`).
