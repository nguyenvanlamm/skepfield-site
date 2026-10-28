# Search Optimization: https://nguyenvanlamm.github.io/skepfield-site/

Run: search-optimizer 1.1.0 · 2026-10-28T13:42:14Z · branch: web (ASO skipped: the App Store listing was done separately)
Evidence: evidence/manifest.json · scan case: B (scan deferred to design-optimizer)
Members: seo-ai-optimizer √ (0 critical before and after; 8 warnings → 0 on indexable pages) · website-agent-readiness — skipped (scan owned by design-optimizer, next stage) · viral-product-evaluator — skipped (virality audited by design-optimizer, next stage) · aso-marketing — skipped (branch not reached)

## Summary
- Agent-readiness score: not scanned in this run
- SEO before: 0 critical · 8 warning · 4 info (audit_seo.py on commit 22ce958)
- SEO after: 0 critical · 3 warning · 2 info, all on the intentional noindex 404.html or the deprecated ai-plugin.json; index, privacy and support have 0 issues
- Findings: 0 P0 · 3 P1 · 5 P2 · 2 P3, all fixed in this run except the two marked "caller" (host-root repo) and one note for the owner

## Web findings

| ID | Pri | Check | Finding | Evidence | Owner | Also reported by | Fix route |
|---|---|---|---|---|---|---|---|
| S-01 | P1 | robots-sitemap | No sitemap.xml for the site; host-root robots.txt lists no Skepfield sitemap | live /sitemap.xml 404; evidence robots.txt lines 6-19 | seo-ai-optimizer | — | Fixed: sitemap.xml added. Caller: add `Sitemap: https://nguyenvanlamm.github.io/skepfield-site/sitemap.xml` to the root robots.txt |
| S-02 | P1 | structured-data | No JSON-LD on any page | audit_seo.py | seo-ai-optimizer | — | Fixed: WebSite + VideoGame/MobileApplication (iOS, no offers, no rating) on index; WebPage on privacy; ContactPage on support |
| S-03 | P1 | llms-txt | No llms.txt; root llms.txt has no Skepfield entry | live /skepfield-site/llms.txt 404; evidence llms.txt | seo-ai-optimizer | — | Fixed: llms.txt added. Caller: add the Skepfield line to the root llms.txt |
| S-04 | P2 | meta-tags | Home meta description 221 chars | index.html:7 | seo-ai-optimizer | — | Fixed: 158 chars |
| S-05 | P2 | meta-tags | og:image is a 390×844 portrait, twitter:card summary | index.html:18-22 | seo-ai-optimizer | — | Fixed: assets/share-card.jpg 1200×630 (approved palette, Alegreya, hero headline, real screenshot), summary_large_image |
| S-06 | P2 | meta-tags | privacy and support have no Open Graph or Twitter tags | audit_seo.py | seo-ai-optimizer | — | Fixed |
| S-07 | P2 | crawler-access | No robots.txt in the site (host-root one allows all bots) | audit_seo.py; evidence robots.txt | seo-ai-optimizer | — | Fixed: documenting copy; only the host-root robots.txt is read by crawlers |
| S-08 | P2 | robots-sitemap | No custom 404 for the project path | repo listing | seo-ai-optimizer | — | Fixed: 404.html, noindex, absolute /skepfield-site/ links |
| S-09 | P3 | meta-tags | index.html body says stones work "like the numbers in Minesweeper" (another game named in approved copy) | index.html rules section | seo-ai-optimizer | — | Not changed (approved copy, not an SEO defect); owner decides |
| S-10 | P3 | llms-txt | No llms-full.txt | — | seo-ai-optimizer | — | Skipped: 3 short pages, llms.txt carries every fact; Markdown page copies are the markdown-pages check (design-optimizer) |

## Skipped (owned elsewhere)
| Check | Skipped by | Owner |
|---|---|---|
| agent-readiness-scan | seo-ai-optimizer (Step 8) | design-optimizer (next pipeline stage, scan approved at G4 2026-10-28) |

## Not covered
| Check | Reason |
|---|---|
| markdown-pages | Needs the isitagentready.com scan, which design-optimizer runs next |
| ai-actions | No web-branch member evaluates it; design-optimizer covers it next |
| virality | viral-product-evaluator skipped; design-optimizer audits virality next |
| store-listing | ASO out of scope (listing done separately, app not live) |

## Member reports
- reports/seo-ai-optimizer/seo-audit-report.md

## Next step
Caller: in repo nguyenvanlamm.github.io add the sitemap line to robots.txt and the Skepfield line to llms.txt; merge and deploy this branch; then design-optimizer runs the scan. The scan will be the first agent-readiness score for this site.
