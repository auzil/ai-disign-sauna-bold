# Lumen Private Spa — variant b-bold

## Direction in one sentence

Forestis' bone page and candle-dark photography with Trudon's serif caps + italic line, disciplined everywhere except one bold move: the price section is a day passing — the page itself goes from cool morning light to warm day, amber dusk, candle-dark evening and blue-black night as you scroll through Morning / Day / Evening / Night.

## Starting point

No library direction fits (dark-poster is the opposite). Built from the Forestis captures (desktop-fold, desktop-01..03, mobile-fold, mobile-02) and Trudon fold (desktop + mobile): "Bone & Flame" from REFERENCES.md.

## Tokens (CSS custom properties, named for Tailwind v4 `@theme`)

| Token | Value | Role |
|---|---|---|
| `--color-bone` | `#F2F1EB` | page, light sections (Forestis bg) |
| `--color-ink` | `#333333` | text on light (Forestis text, not black) ≈ 11:1 on bone |
| `--color-ink-soft` | `#5E5B55` | secondary text on light ≈ 6:1 |
| `--color-night` | `#07131A` | dark sections, night tier, hero shade (Forestis photo shadow) |
| `--color-flame` | `#E7B685` | the one accent — only on night/photo (never text on bone, 1.8:1) |
| `--color-morning` | `#E2E5E3` | tier band: cool first light |
| `--color-day` | `#F7F2E7` | tier band: warm daylight |
| `--color-dusk` | `#A9826A` | gradient stop only, between day and evening |
| `--color-evening` | `#2A1E18` | tier band: candle-dark evening |
| `--color-on-dark` | `#F2F1EB` / soft `rgb(242 241 235 / .74)` | text on dark |
| rules | `rgb(51 51 51 / .18)` light, `rgb(242 241 235 / .22)` dark | 1 px hairlines only |

Radius 0 everywhere. No shadows, no borders around blocks, no texture (Forestis has none).

## Type

- **Display / headings: EB Garamond** (Google Fonts, SIL OFL). Reason: closest free cut to Trudon's Garamond caps headline + italic line; calm, classical, not a high-contrast Didone (keeps away from the "cream + high-contrast serif" default). Latin Extended covers Czech (ě š č ř ž ý á í é ů ú ň ť ď). OpenType `lnum` + `tnum` present — prices use `font-variant-numeric: lining-nums tabular-nums` (default figures are oldstyle).
- **Body / UI: Jost** 300/400/500 (Google Fonts, SIL OFL). Reason: geometric-humanist light sans in the spirit of Forestis' Brandon-like body; light weight, open tracking. Latin Extended (Czech) checked.
- Caps are used only for H1/H2 and the wordmark (Trudon), never as eyebrow labels. Under every caps heading: one italic serif line (Trudon). No mono anywhere.

Scale (fluid): `--text-display` H1 clamp(1.875rem, 3.2vw, 3.25rem) caps 500 +.02em · `--text-h2` clamp(1.625rem, 2.6vw, 2.625rem) caps 400 +.03em · `--text-tier` clamp(4.25rem, 10vw, 10rem) caps 400 (the bold-move scale, tier names only) · `--text-lede` italic clamp(1.1875rem, 1.6vw, 1.5rem) · `--text-price` clamp(2.5rem, 4vw, 3.75rem) · `--text-body` clamp(1.0625rem, 1.1vw, 1.1875rem)/1.65 Jost 300 · `--text-ui` .9375rem Jost 400 · `--text-fine` .875rem.

## Layout

Forestis proportions: 1080 px image column (`--container-page: 67.5rem`), 2-column grids with 20 px gutter and mixed ratios (4:5, 1:1, 3:2), text centred at ~44rem measure below image groups, ~200 px air between blocks (`--space-section`). The 24 h section breaks the column on purpose: full-bleed colour bands, sticky left aside.

## Section map

| # | id / data-section | Job |
|---|---|---|
| 1 | header | Menu, wordmark centred, EN/CS, Gift voucher, **Book a slot** (always visible) |
| 2 | hero | what + reassurance + from-price + Book a slot / gift; full-bleed candle photo |
| 3 | intro | "Nobody else inside" — concept + 4 plain facts (private, 24/7, bring nothing, 18+) |
| 4 | space | Forestis staggered grid: sauna, jacuzzi, shower, relax zone + what's included (robes) |
| 5 | day (**bold move**) | prices by time of day: 4 full-bleed light bands; sticky aside with rail, from-price, Book a slot |
| 6 | addons | prosecco, fruit plate, massage, extra hour — "add in the calendar" |
| 7 | how | 4 real steps (numbered, it's a sequence): book, code, let yourselves in, leave |
| 8 | occasions | one centred serif line, Forestis quote scale — couples first, birthdays, girls' night |
| 9 | voucher | 3:2 photo band + text + "Buy a gift voucher" |
| 10 | faq | `<details>`: bring, privacy, night, entry, 18+, extra guests, cancellation, health |
| 11 | book | final dark photo band + Book a slot |
| 12 | footer | contacts (placeholders flagged), language, legal |
| + | floating WhatsApp (desktop), sticky bottom bar (mobile: WhatsApp cell + Book a slot), full-screen menu |

## Signature moment — "A day in four lights"

Section `day`: four full-bleed bands, Morning / Day / Evening / Night. Each band's background is its tier colour and the band tops blend from the previous one (cool pale → warm white → amber dusk → candle brown → blue-black), so plain scrolling *is* the day passing — no animation needed for the core effect, works with reduced motion and in full-page screenshots. Each band: tier name at radical serif scale (≈10vw caps), one italic line, two sentences, one photo whose light matches the hour (bright rain shower → sauna wood → lamp-lit relax zone → candle in black water). A sticky aside (desktop left column, mobile top rail) holds the four tier names with the current one active, the SAMPLE "from 1 990 Kč / 2 h for two", "exact price for each time of day is in the calendar", and Book a slot. A soft light disc ("the sun", then a flame glow at night) drifts across the bands with scroll (GSAP scrub, transform only). No tier prices, no hour boundaries — structure only.

## Motion plan

1. Load: hero photo scale 1.06 → 1 (2.4 s, power2.out); H1 line-mask reveal (SplitText, expo.out, .9 s, stagger .08); offer stack opacity 0 → 1 after.
2. Space grid photos: one clip-path reveal on first enter (inset from bottom), no fade-up on text.
3. Day section: aside tone + rail switch (CSS transition .6 s on tier change); light disc scrubbed across the section (transform only).
4. Menu: clip-path wipe .5 s power3.inOut, links stagger.
Everything in `gsap.matchMedia('(prefers-reduced-motion: no-preference)')`; initial hidden states set by GSAP only.

## Photos (all temporary, AI-generated, flagged)

| Slot | File | Why |
|---|---|---|
| hero desktop | `media/temp/hero-3.jpg` | orchestrator pick; dark wall left for the offer stack |
| hero mobile | `media/temp/hero-tall-2.jpg` | matches hero-3; steam top for headline |
| space: sauna | `sauna-2.jpg` | darker, door frame, hidden light strip |
| space: jacuzzi | `water-1.jpg` | almost abstract, candle streak, Forestis restraint |
| space: shower | `shower-1.jpg` | dark stone, misted glass |
| space: relax | `relax-2.jpg` | symmetrical loungers, stone wall — strongest Forestis frame |
| included | `robes-1.jpg` | robes, slippers, one candle |
| day: Morning | `shower-2.jpg` | brightest, white rain light = first light |
| day: Day | `sauna-1.jpg` (tight crop) | warm wood, brighter than sauna-2 |
| day: Evening | `relax-1.jpg` | lamp-lit, robes, stone wall |
| day: Night | `water-2.jpg` | candle in black water, brass spout |
| addons | `addons-1.jpg` | darker, Trudon brass + flame reflections |
| how it works | `door-1.jpg` | night courtyard door + keypad = self check-in |
| voucher | `voucher-2.jpg` | cleaner envelope on robe |
| final CTA | `hero-1.jpg` | wide candle-lit jacuzzi, couple far right |

## Hero wireframes

Desktop 1440×900 (photo 100%, Trudon bottom-left placement, Forestis element count):
```
+--------------------------------------------------------------------------------+
| Menu  EN/CS                    L U M E N              Gift voucher [Book a slot]|
|                                                                                |
|  (dark stone wall)                       (bronze mirror, steam, candles)       |
|                                                                                |
|                                                   (couple from behind)         |
|  A WHOLE SPA,                                                                  |
|  JUST FOR THE TWO OF YOU                                                       |
|  Private sauna, jacuzzi and relax room in Prague. Nobody else inside.          |
|  from 1 990 Kč   2 hours for two                                               |
|  [ Book a slot ]   Give it as a gift                                           |
|  Open 24/7, night slots too     Towels, robes, slippers included     18+       |
+--------------------------------------------------------------------------------+
```
Mobile 390×844 (photo 100%; sticky bar appears after the hero):
```
+------------------------------+
| Menu    L U M E N   [Book]   |
|                              |
|  A WHOLE SPA,                |
|  JUST FOR THE                |
|  TWO OF YOU                  |
|  italic: sauna, jacuzzi...   |
|        (steam, mirror)       |
|        (couple, candles)     |
|  from 1 990 Kč  2 h for two  |
|  [  Book a slot  ]           |
|  Give it as a gift           |
|  24/7 incl. night  Robes...  |
+------------------------------+
```

## Anti-pattern check (changed defaults)

- Bone + serif + warm accent is close to the "cream + serif + orange" default → flame is never used on bone (only glow on night/photos), ink is Forestis grey not black, serif is Garamond (not high-contrast), photography carries the colour.
- No eyebrows, no mono, no numbering except the real 4-step "how it works", no `→` on links, no middle-dot meta strings, no bordered boxes/cards, no stamps/tickets — the voucher is a photo, not a "ticket" UI.
- Facts are plain text, not icon tiles. No reviews/ratings/stats. No fade-up on every section.
- Hero headline is a value statement, not "Welcome to Lumen".
