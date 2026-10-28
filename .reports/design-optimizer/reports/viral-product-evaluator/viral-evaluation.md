# Viral Product Evaluation: Skepfield

```
Result: PASS — all 32 principles scored from full evidence; report written
Virality Score: 55/100 — Needs work
Product: Skepfield, an unreleased iOS beehive logic puzzle (Flutter): one straw hive per plot, numbered stones count the hives around them
Evaluated: evidence-dir (page.html = live https://nguyenvanlamm.github.io/skepfield-site/, head.json, screenshots) · codebase /home/lam/Documents/projects/skepfield (lib/ui, lib/game, pubspec.yaml, docs/APP-STORE-CONNECT.md, store/listing-en-US.md), read-only
Orchestrated by: design-optimizer

PASS: 10/32   PARTIAL: 15/32   FAIL: 7/32
```

Score from `scripts/virality_score.py` over `verdicts.json` (in this folder): 17.5 points.

Read the score in context: 6 of the 7 FAILs (#1, #8, #14, #15, #29, #31) and part of the PARTIALs come from fixed product decisions (a free season plus a free daily field, no price set yet, unreleased so no players to quote, no other games may be named). The site's fixable gaps are the hero copy, the inert CTA and the missing share loop in the game.

## Meta tags check (owned here): PASS

Verified in the files, not assumed from the search-optimizer report:

- index.html:6 title "Skepfield: a calm beehive logic puzzle for iPhone" (49 characters); :7 meta description (158 characters, per search-optimizer S-04), plain and accurate; :8 canonical; :9 robots `index, follow, max-image-preview:large`.
- index.html:14-24 Open Graph complete: type, site_name, locale, title, description, url, image, image:type, image:width 1200, image:height 630, image:alt. :25-29 Twitter: `summary_large_image`, title, description, image, image:alt.
- assets/share-card.jpg is really 1200×630 (read from the JPEG SOF header, 86.8 KB), so the declared size matches the file.
- privacy.html:13-23 and support.html:13-23: og title/description/url/image/width/height/alt and `twitter:card summary_large_image`; Twitter falls back to the og tags for title/description/image, so nothing is missing. 404.html:8 is `noindex` (no social tags needed).
- Optional only: privacy/support omit `og:image:type` (index has it). No fix needed.

## Scorecard

### A. Pricing & monetization
```
FAIL  #1  No free plan ········· "Free to start, yours to keep" / "Play for nothing, for good": Spring's 40 fields + a daily field free forever (index.html:256-265); docs/APP-STORE-CONNECT.md:17 "Free (with in-app purchases)". Deliberate.
FAIL  #8  Hard paywall ········· Full value (Spring + daily + 3 Almanac pages/day) with no payment ask (index.html:260-265). Deliberate.
PASS  #12 Popcorn pricing ······ Two cards: Free / Buy once (index.html:258, :268); every paid item one flat SKU (docs/APP-STORE-CONNECT.md:35-38).
PART  #16 Pricing unmissable ··· Clear #seasons section, but header nav is only Rules + Support (index.html:202) and no price figure is shown (prices not public yet).
PASS  #27 No subscription ······ "Seasons are one-time unlocks, in any order. No subscription." (index.html:277); Products: 3 non-consumables + 1 consumable (lib/game/wallet.dart:8-11).
PART  #32 Priced above comps ··· Planned USD 1.99 per 40-field season / Kit (docs/APP-STORE-CONNECT.md:35-38): mid-to-low for paid puzzle content, not pitched as cheap.   ⚠ check category price points
```

### B. Hero & headline
```
PART  #20 Sellable from hero ··· Label + H1 + sub make "logic puzzle for iPhone" clear; hero image is the home menu (home.webp, index.html:217), not the puzzle board; CTA is a status, not an action.   ⚠ stranger test on mobile fold
PASS  #7  Fifth-grade headline · "Find the one place each hive belongs." (index.html:209): plain words, 7 words.
PART  #18 Emotional headline ··· Quiet intrigue ("the one place"), but it describes the task, no wow or relief.   ⚠ gut-check the feeling
PART  #17 Memorable headline ··· Short and concrete, but not surprising enough to repeat tomorrow.   ⚠ ask a cold reader next day
PART  #3  Numbers ·············· Hero copy has no number (index.html:208-214); numbers live below (40 fields, 5×5-10×10, one to five minutes, :233, :262). "160 fields" never appears on the page.
PART  #24 Human desire ········· The outcome ("A few quiet minutes", index.html:224; "calm") sits in section 2; the hero sub restates the rules (index.html:210).   ⚠ judge outcome vs feature lead
```

### C. Message clarity & focus
```
PASS  #11 Does one thing ······· One puzzle type; seasons, daily field and Almanac all serve it (index.html:229-277; lib/game/seasons.dart).   ⚠ confirm no bolt-on blur
PASS  #30 Under 10 words ······· "Beehive logic puzzle for iPhone" (5 words, hero label, index.html:208); "A beehive logic puzzle for iPhone." (index.html:302).
PASS  #6  One idea per screen ·· Hero / How it plays / Rules / Seasons / No ads / End: one message each.   ⚠ scroll mobile.png to confirm
PART  #22 One CTA ·············· One message repeated ("Coming soon to the App Store", index.html:211, :303), no competing CTAs, but it is a <p>, not a link: the visitor has no action at all.
FAIL  #28 CTA says what's next · No actionable CTA exists; the pill states a status. (No App Store link exists yet: constraint.)
```

### D. Proof & differentiation
```
PART  #21 Empathy first ········ Only the trust chips "No ads / No tracking" (index.html:213) hint at the pain; no line names what annoys puzzle players (ads between levels, energy timers, guessing). The listing's "No energy, no timers to wait out" (store/listing-en-US.md:72) is not on the site.   ⚠ judge framing
PASS  #9  Copy only you'd write  "A hive in the wrong cell sends a bee away. Lose all three and the bees move on" (index.html:231), Smokers, Spare Bees, the Almanac: specific to this game.   ⚠ voice check
FAIL  #14 Customer copy ········ No player voice anywhere (unreleased; no TestFlight quotes).
PASS  #26 No weak words ········ Only hedge-list hit is "up to 9 of each" (index.html:265), a factual cap, not a hedge; claims are falsifiable ("exactly one solution", :233).
FAIL  #29 Testimonials ········· None (unreleased, no ratings or player counts).
FAIL  #31 Compares ············· No comparison; the only other game named is the rules analogy (index.html:249), not an alternative. Naming other games is off-limits, so only an unnamed "what's left out" contrast is possible.
PART  #19 Never seen before ···· Known one-per-region grid genre with one labelled twist: numbered stones (index.html:247 "The twist").   ⚠ novelty is taste
```

### E. Show, don't tell
```
PASS  #10 Product first ········ Phone screenshot in the hero (index.html:216-218), visible at the mobile fold (mobile-fold.png).
PART  #25 Try before buying ···· Static screenshots only (home.webp, game.webp); nothing playable on the page. The app itself is try-first (free season), but the page is not.
FAIL  #15 Founder visible ······ "© 2026 Skepfield" + a mailto (index.html:309-310); no name, face or voice.   ⚠ owner's choice
```

### F. Visual & shareability
```
PART  #2  Three colors ········· Sage bg, ink text, beeswax CTA, plus hedgerow green panels (index.html:72-74, :137, :166); beeswax also on every hex bullet and rule number, so the accent is not CTA-only. Approved look, fixed.   ⚠ visual
PART  #4  Shareable footer ····· End block: mark, "Skepfield", "A beehive logic puzzle for iPhone.", "Coming soon" (index.html:299-304): tidy identity, nothing quotable.   ⚠ judge closing moment
PASS  #5  OG thumbnail ········· og/twitter image present, 1200×630 verified, big Alegreya headline + a real 7×7 board + beeswax pill (assets/share-card.jpg): one idea, readable at thumbnail size.   ⚠ eyeball in a real feed preview
PART  #23 Memorable name ······· "Skepfield": "field" is known, "skep" (old word for a straw beehive) is not, and the site never explains it.   ⚠ say-it-aloud test
```

### G. Distribution context
```
PART  #13 Rides a wave ········· Daily logic grids are a live habit and the game has a new 8×8 field every day (lib/game/seasons.dart; listing subtitle "Daily grid puzzle, no guessing"), but the site mentions it only as a chip and a list item (index.html:213, :263), and the solved card has no way to share a daily result (lib/ui/field_cards.dart:72-152).   ⚠ trend judgment
```

## Top fixes (impact × ease)

Tags: **[site, look-preserving]** = copy/markup/meta only · **[site, owner proposal]** = changes the look or adds a section · **[game app, owner proposal]** = out of scope for this site run.

```
V-01 (P1). Rewrite the hero sub to sell the calm minutes, with numbers and the daily field — fixes #3, #24, #13, #20, #18   [site, look-preserving]
     Now:    "Skepfield is a calm logic puzzle on a patchwork field. Every plot gets one straw hive, and numbered field stones count the hives around them." (index.html:210)
     Change: Keep the H1. Sub: "One to five quiet minutes of pure logic: a new 8×8 field every day, and 160 more across four seasons. One straw hive per plot; numbered stones count the hives around them."
     Why:    The hero carries the sale; it should name the outcome (a calm break) and two concrete numbers, and lead with the daily habit. All facts are in the listing and lib/game/seasons.dart.

V-02 (P1). Add "Share" to the solved card of Today's field — fixes #13 (and feeds #29/#14 later)   [game app, owner proposal, out of scope here]
     Now:    _SolvedCard shows "Field tended", "Time m:ss", the Clean badge and Fields / Next field; no share (lib/ui/field_cards.dart:72-152); no share package in pubspec.yaml:18-26.
     Change: For the daily field only, a "Share" pill that copies a spoiler-free text via Flutter's built-in Clipboard (no new dependency, nothing sent anywhere), e.g. "Skepfield · Today's field · Wed 28 Oct · 2:41 · Clean (no bee lost) · nguyenvanlamm.github.io/skepfield-site/". UI-only; Daily/generator output stays identical.
     Why:    A same-for-everyone daily puzzle spreads by players posting their result; today that loop does not exist.

V-03 (P1). Give the CTA an action — fixes #28, #22, #20   [site, look-preserving; launch-day part waits for the App Store link]
     Now:    <p class="soon">Coming soon to the App Store</p> twice, not clickable (index.html:211, :303).
     Change: Launch day: make both pills <a> to the App Store page, label "Play today's field free on the App Store". Before launch (owner opt-in, no backend): wrap the hero pill in a mailto to the existing contact address with subject "Tell me when Skepfield is out" and a one-line note "Tap to get one email on launch day"; the owner answers those by hand.
     Why:    A visitor who wants it now has nothing to do; the CTA should say what happens next.

V-04 (P2). Name the pain and the unnamed contrast in the "Nothing in the way" list — fixes #21, #31, #24   [site, look-preserving]
     Now:    List says no ads/analytics/tracking, no account, offline, App Store only for purchases (index.html:290-293).
     Change: Add one <li>: "No energy bar, no timers to wait out, no guessing." (all true: store/listing-en-US.md:43, :72). Optionally change the hero chip "No tracking" to "No guessing".
     Why:    Puzzle players know what annoys them in other apps; naming it (without naming anyone) makes the switch obvious.

V-05 (P2). Tell the name's story and end on a line worth quoting — fixes #23, #4, #17   [site, look-preserving]
     Now:    End lede "A beehive logic puzzle for iPhone." (index.html:302); "skep" is never explained.
     Change: End lede: "A skep is an old straw beehive. Set the first one and see where the field leads." (the second sentence is the listing's closing line, store/listing-en-US.md:77).
     Why:    A one-line meaning makes the invented name memorable and gives the page a closing line to share.

V-06 (P2). Put a maker in the footer — fixes #15   [site, look-preserving; owner confirms name and wording]
     Now:    "© 2026 Skepfield" (index.html:309).
     Change: "© 2026 Skepfield · Made by Nguyen Van Lam" (name taken from the bundle id com.nguyenvanlam in lib/game/wallet.dart:8; owner confirms or picks the form).
     Why:    A real person behind a quiet, ad-free game is part of its trust story.

V-07 (P3). Collect 2-3 TestFlight player lines and show them — fixes #29, #14   [site, owner proposal: adds a section]
     Now:    No player voice on the page.
     Change: After TestFlight, ask testers for one sentence plus permission to use a first name; add a small "From the first beekeepers" row before the end block, and reuse their words in V-01/V-04 copy.
     Why:    Proof from players beats any claim; it is the biggest missing proof lever once players exist.

V-08 (P3). Add "Seasons" to the header nav, and the price once it is set — fixes #16   [site, owner proposal: header may crowd at 390 px]
     Now:    Nav "Rules", "Support" (index.html:202); "Buy once" card has no figure (index.html:269).
     Change: Nav link "Seasons" → #seasons (verify the 390 px header still fits on one line); when prices are final, add "USD 1.99 each, paid once" under "Buy once".
     Why:    Pricing that is one tap away and concrete removes a reason to bounce.

V-09 (P3). Let visitors play one field on the page — fixes #25, #19   [site, owner proposal: adds a section; needs a game web build]
     Now:    Only static screenshots (index.html:217, :227).
     Change: A small embedded web build of one fixed Spring field (stones from field 4) under "How it plays", ending with the V-03 CTA.
     Why:    Trying the twist is more convincing than reading about it; larger effort, so last.
```

Not fixed on purpose: #1, #8, #32 (free season + free daily field and the planned price are the product's acquisition design, so no change is proposed) and #2 (approved palette, fixed). Meta tags: no fix needed (verdict PASS above).

## What's already working
- #5 Share card: real 1200×630 JPEG, big headline, real board, correct og/twitter markup on all indexable pages.
- #7 Plain headline: "Find the one place each hive belongs."
- #9 Specific copy: bees that move on, Smokers, the Almanac.
- #10 Product shown in the hero, above the mobile fold.
- #11 / #30 One clear job, said in 5 words.
- #12 / #27 Two simple cards, buy once, "No subscription" stated.
- #26 Falsifiable claims ("exactly one solution", "one to five minutes").
- #6 Clean one-idea sections.

## Caveats
- Low-confidence (judgment/visual), for a human to eyeball: #2 accent spread, #4 closing moment, #5 share card in a real feed preview, #6 section rhythm on mobile, #9 voice, #11 focus, #13 trend fit, #15 owner presence (the owner's choice), #17 / #18 headline stickiness and feeling, #19 novelty of the stones twist, #20 stranger test on mobile-fold.png, #21 problem framing, #23 name, #24 outcome lead, #32 price vs category (no competitor named, by rule).
- Strategic deviations (scored as written): free season and free daily field (#1, #8); unreleased, so no testimonials, customer quotes or App Store link (#14, #22, #28, #29); other games may not be named (#31); approved look fixed (#2).
- Copy facts used in fixes come from store/listing-en-US.md (draft, pending the owner's G4 approval) and lib/game; re-check if the listing changes.
- skip-checks: none given. This run owns `virality` and `meta-tags` (manifest `owners`).
- Repo sync: the output path is inside the git worktree (untracked `.reports/`), but sync was not run: the orchestrator forbids changing the checkout, and the manifest records the branch was fast-forwarded to origin/main 100ab67 (= live) before capture. Only this report and `verdicts.json` were written.
- /browse was not used: page.html and screenshots come from the orchestrator's evidence-dir (Chrome headless capture); page.html is byte-identical to the worktree's index.html.
