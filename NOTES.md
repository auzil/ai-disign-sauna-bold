# b-bold — notes

## What this variant tries

Forestis' discipline (bone page, soft ink, dark candle-lit photos in a 1080 px two-column grid, lots of air, radius 0, no boxes) with Trudon's type pairing (Garamond caps headline + one italic serif line). Everything stays quiet except **one bold move**: the price section is a day passing. The section is four full-bleed bands, Morning / Day / Evening / Night. Each blends from the previous one (cool pale, warm white, amber dusk, candle-brown, blue-black), so plain scrolling darkens the page from morning into night. Each band has its tier name at a radical serif scale (about 10vw caps) and a photo whose light matches the hour, and ends in a "Book a morning / daytime / evening / night slot" link. A sticky aside (a top rail on mobile) shows the four tiers, the SAMPLE from-price and Book a slot. The core effect is CSS gradients, so it works with reduced motion, without JS and in full-page screenshots. No tier prices and no hour boundaries are shown: the copy says each time of day has its own price, shown in the calendar.

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

## Round 1 changes (critique round 1, fix 1 of 2)

Ordered as in the punch list. Verified at 390×844 and 1440×900 with full-page shots (`shots/`) and viewport shots in every band and through the dusk blend. Contrast was measured on rendered pixels in the core of each line of text, every 12 px of scroll.

1. **Bold move.**
   - Bands are now `min-height: 72vh` (was 100vh) with 12vh/10vh padding, and band photos are 22rem wide (was 27rem). At 390 the band photo is 3:2. Page height at 1440 dropped from 15 046 to 13 871 px.
   - Morning is cool blue-grey `--color-morning: #D9E0E3`. Day is warmer `--color-day: #F6EDDA`. They now read as two different lights.
   - Each band has a "Book a morning / daytime / evening / night slot" link to `#booking-TODO`. Per the orchestrator, there are no per-tier price lines and no reserved space for them; per-tier SAMPLE prices are an owner question in TODO-OWNER.md.
   - Day band uses a new high-key sauna photo (`media/day-sauna-2.jpg`, no candles).
   - Morning uses `shower-2` cropped tight on the rain head (scale 2 on desktop; on mobile, top-anchored at scale 1.6). It is lightened with `brightness(1.08) saturate(.9)`. The crop removes the smear on the glass and differs clearly from `shower-1` in the grid.
2. **Contrast.**
   - Inactive rail links are now `--color-ink-soft` on light (about 5:1 on morning and 6:1 on day). On dark they use a new token, `--color-on-dark-muted` (bone at .86), instead of the opacity fade. At .74 they measured 2.7–2.9:1 over the dusk tone.
   - The dusk blend is now `day → dusk at 3vh → evening at 24vh`, with tokens `--dusk-at` / `--evening-at`. The light-to-mid jump is short, and the amber-to-brown tail under "EVENING" is kept.
   - `--color-dusk` is darker: `#9A735C`, bone on it ≈ 3.7:1.
   - Rail links and aside items now flip tone one by one, at 95% of the `--dusk-at` stop (where ink and bone contrast cross), instead of as one block 24% into the band.
   - Measured result: each rail line drops below 3:1 for only about 2 of 106 scroll samples (≈24 px of scroll, the moment the ramp crosses the glyphs). Before, it sat at 1.8–2.1:1 across the whole blend. Aside price text drops below 3:1 for one sample.
   - The mobile final band now has a people-free photo and a bottom shade that reaches `--color-shade` at 38%. Worst case under the headline is 10.1:1.
3. **Photo artifacts and repeats.** `hero-1` (ghost face) is no longer used. Four photos were generated in this variant (`shotlist.json`, `media/`, one run, no regenerations):
   - `final-empty` (16:9, reference hero-3, no people, mirror shows only steam and candles) for the final band
   - `day-sauna` (high-key)
   - `relax-empty` (reference relax-2, empty, different framing) for Evening, replacing `relax-1`, the same couple as `relax-2`
   - `night-candle` (reference hero-3, one candle and black water) for Night, replacing `water-2`, which after the shared regeneration is nearly identical to `water-1` in the grid

   Picks: final-empty-1 (cleaner mirror), day-sauna-2 (no thermometer scale, bench layout closest to sauna-2), relax-empty-2 (most different framing from relax-2), night-candle-2 (darker, clearer single streak).
4. **Closing headline.** "Book the whole spa for two", with the italic line "Free slots are in the calendar, day and night." (lede `max-width: 26rem`).
5. **Heading formula.** The italic line was removed from intro, space, add-ons, how it works and FAQ. It stays on the hero, `#prices`, `#voucher` and the final band. The intro's "two or three hours" fact moved into the body sentence.
6. **WhatsApp float.** An IntersectionObserver adds `.is-tucked` while `.facts`, `.day__body`, `.final` or the footer is in view. Checked at 1440 on the facts row, in the bands, on the final band and on the footer.
7. **Unconfirmed copy.**
   - Dropped "rain shower", "by candlelight", "loungers, linen, a candle and a glass of water", "Chilled, with two glasses, ready by the jacuzzi" and "Fresh seasonal fruit".
   - Booking behaviour now reads "confirmed when you book / at booking / when you buy". The door code line is "You get a personal door code for your booking" (flagged).
   - The intro uses the tier names "Morning, day, evening and night".
8. **Paper trail.**
   - Added `TODO-OWNER.md`.
   - Both email links go to `#email-TODO` (sample text kept, flagged).
   - The footer shows "Prague" plus "Open in maps", with no district.
   - The EN/CS switch, "Česky", legal links and the menu wordmark are flagged.
9. **Sun disc** deleted: markup, CSS and the GSAP scrub. The colour bands carry the move, and nothing blends on scroll any more.
10. **Small craft.**
    - The price note in `#prices` is `--text-body` (17 px at 390).
    - Footer legal row uses `align-items: baseline`.
    - The final photo fades to full `--color-night` at the bottom, with no hard edge above the footer.
    - On desktop, the header "Gift voucher" link is hidden over the hero, so it doesn't repeat "Give it as a gift". It comes back with the solid header.
    - Hero image `object-position` moved to 45%, so "JUST FOR THE TWO OF YOU" now ends about 55 px from the man's back (was about 30).

### Still open
- The four tier prices (owner question; bands keep only the booking link).
- A rail line can still dip below 3:1 for roughly 24 px of scroll as the light-to-dusk ramp crosses it. This is the cost of a blended background behind fixed text. Removing it fully would need a hard edge or a backing behind the rail, and either would undo the blend the critique asked to protect.
- The final band and the hero are the same room (hero with the couple, final empty). That is intentional now: it reads as "the same room, yours". It is no longer a repeated couple scene.

## Manual review fixes

- Rail links (Morning / Day / Evening / Night) no longer use plain anchor jumps, which landed each band's top under the header and mobile rail, at a different place per band (the evening/night bands have more top padding for the dusk blend). A click now scrolls the tier **name** to one fixed spot: compact header + sticky rail + 1.5rem on mobile (name at 133 px at 390), compact header + 12vh on desktop (172 px at 1440). The rail highlights the clicked tier straight away and doesn't flicker through the bands passed on the way; it resyncs with the band at the viewport middle when the scroll ends. Smooth scroll, instant with reduced motion. Checked by clicking all four in shuffled order at 390 and 1440, both motion modes.
- Horizontal scroll on 360px phones (Samsung S24): the tier names in the 24-hour bands were set at the 4.25rem minimum, so "MORNING" (~347px) plus side padding needed 384px; the single-column grid of `.day__body` grew to fit and widened the whole page, and with the page pannable the fixed header shifted on scroll. Fix: tier names scale with the screen on mobile (`min(var(--text-tier), 16vw)`), the grid column is `minmax(0, 1fr)`, and `body { overflow-x: clip }` as a safety net. Page width now equals the viewport at 320 / 360 / 384 / 390 / 412 even without the safety net; tier jumps still land at the same spot at 360.
