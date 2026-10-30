# b-bold — notes

## What this variant tries

Forestis' discipline (bone page, soft ink, dark candle-lit photos in a 1080 px two-column grid, lots of air, radius 0, no boxes) with Trudon's type pairing (Garamond caps headline + one italic serif line). Everything stays quiet except **one bold move**: the price section is a day passing. The section is four full-bleed bands, Morning / Day / Evening / Night. Each blends from the previous one (cool pale, warm white, amber dusk, candle-brown, blue-black), so plain scrolling darkens the page from morning into night. Each band has its tier name at a radical serif scale (about 10vw caps) and a photo whose light matches the hour. A sticky aside (a top rail on mobile) shows the four tiers, the SAMPLE from-price and Book a slot. A soft light disc drifts across the bands with scroll (GSAP scrub, transform only) and turns into a flame glow at night. The core effect is CSS gradients, so it works with reduced motion, without JS and in full-page screenshots. No tier prices and no hour boundaries are shown: the copy says each time of day has its own price, shown in the calendar.

## Hero vs style reference (Forestis fold, Trudon fold)

| Aspect | Forestis / Trudon | b-bold hero | Decision |
|---|---|---|---|
| Image coverage | 100% desktop, ~81% mobile (Forestis); 96% (Trudon) | 100% both | keep: the candle photo does the selling |
| Elements in fold | 6 (Forestis), ~12 (Trudon) | 11 desktop: menu, lang, wordmark, gift, book, h1, lede, price, CTA, gift link, facts | the offer stack is required by the intake; it is set small and pushed bottom-left like Trudon so the photo stays dominant |
| Headline | light sans ~2.9vw, centred, one line (F); serif caps ~2.8vw + italic line, bottom-left (T) | EB Garamond caps 500, ~3.2vw, two lines broken by meaning, italic line below, bottom-left | Trudon pairing, as the brief allows |
| Header | Menu left, spaced wordmark centre, Request / Book plain text right | Menu + EN/CS left, spaced LUMEN centre, Gift voucher + solid Book a slot right | primary needs a visible block (REFERENCES §2); turns bone with a hairline as soon as you scroll (Forestis behaviour) |
| Contrast aid | none (dark photo) | left and bottom night gradient over the photo | needed for the offer text over steam and water |
| Mobile | headline centre, Scroll cue, sticky icon bar | headline top over the steam, offer at the bottom over dark water, sticky WhatsApp + Book bar after the hero | sell-first: what, from-price, reassurance (24/7, nobody else, robes included, 18+) and Book a slot all in 844 px |
| Mobile first viewport (390×844) | | header Book a slot, H1, lede (private, nobody else inside, day or night), from 1 990 Kč / 2 hours for two, Book a slot, Give it as a gift, Open 24/7, Towels/robes/slippers included, 18+ | all four sell-first items visible |

## Photo choices (all temporary, AI-generated, from `media/temp/`)

- Hero: `hero-3.jpg` desktop / `hero-tall-2.jpg` mobile (orchestrator picks, they match).
- The space grid: `sauna-2` (darker, door frame), `water-1` (near-abstract candle streak), `shower-1` (dark stone, misted glass), `robes-1` (cropped 1:1). Relax band: `relax-2` (symmetrical, the strongest Forestis frame).
- 24 h bands: Morning `shower-2` (brightest, white rain light), Day `sauna-1` (warm wood, cropped tighter so it doesn't repeat `sauna-2`), Evening `relax-1` (wall lamp), Night `water-2` (candle in black water, brass spout).
- Add-ons `addons-1` (darker, more Trudon brass and flame than `-2`). How it works `door-1` (blue night courtyard, keypad). Voucher `voucher-2` (cleaner envelope). Final band `hero-1` (wide, couple far right).
- No regenerations. Known repeat: sauna, shower and relax each appear twice (grid + band). They are different frames of the same rooms, which fits "one space" but is noticeable. Real photos would fix it.
- Images load eagerly in the prototype (27 MB of temp JPGs in total) so the screenshot script captures every one. At port, use next/image lazy loading and sizing.

## Placeholders used (flagged with `data-placeholder` in the HTML)

- Brand name "Lumen" / wordmark (working title, trademark unchecked).
- Price "from 1 990 Kč, 2 hours for two" (SAMPLE). Per-tier prices, hour boundaries, 3 h price, extra-guest surcharge and max guests are not shown; the copy defers to the calendar.
- `#booking-TODO` on every Book a slot (header, hero, aside, final, sticky bar, menu, footer). External calendar URL TODO.
- `#voucher-TODO` (voucher shop). Voucher validity and terms are "shown before you pay".
- `#whatsapp-TODO` (floating button, sticky bar, final band, footer, menu). No number is shown.
- `hello@lumenspa.cz` (SAMPLE email). `#instagram-TODO`, `#map-TODO`.
- "Vinohrady, Prague 2" in the footer (SAMPLE district, address TODO).
- `#lang-cs-TODO` (CS locale not built; switch is visual only).
- `#terms-TODO`, `#privacy-TODO`, `#cookies-TODO`. Company ID is omitted (TODO).
- Copy that depends on owner facts, written so it doesn't claim specifics: door code "sent to you before your slot" (channel and timing TODO), cancellation "shown in the calendar" (TODO), massage "ask for it when you book" (provider TODO), health line in the FAQ (owner must confirm wording), add-on prices "in the calendar".
- Every photo is AI-generated and flagged in alt text ("temporary image"). The footer line says the photos are temporary illustrations.

## Known gaps

- Shared-scene repeats (see photos).
- During the short day-to-evening blend (about 20% of one band's height) the dusk mid-tone gives neither ink nor bone AA contrast. The aside tone switches at the darkest-safe point (24% into the evening band), but a line of rail text can sit on the mid-tone for a moment while scrolling.
- The scrubbed light disc is subtle on purpose. On light bands it is barely visible; if the critic wants the "sun" read more clearly, raise `--sun-opacity` or switch the blend mode.
- The floating WhatsApp button (desktop) can sit over the right end of the facts row when scrolled there. It is small, but it overlaps.
- Full-page screenshots show the sticky aside only at its first position (morning). Viewport shots at each tier were checked by hand (rail and price tone switch correctly; the mobile rail takes the band colour).
- No proof section: there are no real reviews. The FAQ and how-it-works carry the reassurance.
- Tone and colour rely on CSS gradients between tier tokens. The port needs these four tier colours plus `--color-dusk` in `@theme`.
