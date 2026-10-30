# Critique — b-bold — round 2

Verdict: SHIP (rubric: PASS)
Scores: Sells 5 · Fidelity 4 · Distinctiveness 4 · Typography 4 · Imagery 4 · Mobile 4 · Craft 4  (total 29/35)

All screenshots are fresh: full page, fold and reduced motion at 390 and 1440, plus viewport shots in every band. The dusk blend at 1440 was swept every 6 px of scroll (144 steps), measuring contrast for each rail line and aside line on rendered pixels.

Evidence per axis:
- **Sells 5**: the 390×844 fold is unchanged and complete: what, for two, SAMPLE from-price, 24/7, robes included, 18+, Book a slot and a gift path. Each band now ends in "Book a morning / daytime / evening / night slot". The price section dropped from 33% to 28% of the page (3 885 of 13 871 px at 1440). Per-tier prices are excluded by the orchestrator ruling.
- **Fidelity 4**: Forestis discipline everywhere except the deliberate bands: bone page, 1080 px mixed-ratio grid, radius 0, no boxes, low-key photos, generous air. The hero has the same element count as round 1; the desktop header no longer repeats "Gift voucher" over the hero.
- **Distinctiveness 4**: the four bands now read as four lights: cool blue-grey morning (`#D9E0E3`), warm cream day with a high-key sauna, a soft horizon into amber and candle-brown, then blue-black night. The day→evening horizon under the 10vw bone "EVENING" is the memorable moment. With the sun disc gone, nothing on the page is decoration.
- **Typography 4**: the caps + italic-line formula is gone from intro, space, add-ons, how it works and FAQ. It stays on the hero, prices, voucher and final band, where it earns its place. Inactive rail links use solid soft colours. What's left is two widows (punch list 4).
- **Imagery 4**: the ghost-face photo is out, no couple scene repeats, and the Evening and Night photos are new frames. The final band is the hero room, empty. Remaining: the Day sauna looks like a different room from the grid sauna, and there are faint pale shapes in the final band's mirror (punch list 1–2).
- **Mobile 4**: each band fits roughly one screen (3:2 photo, name, two lines, link). The rail takes the band colour, and the sticky WhatsApp + Book bar is present throughout. The final band's mobile crop is mostly blurred mirror.
- **Craft 4**: reduced motion is complete, and the full-page capture now includes the final photo. The WhatsApp float tucks away over the facts row, bands, final band and footer (checked: absent in the facts, morning, day, evening, night and final shots). `TODO-OWNER.md` is thorough. Email links go to `#email-TODO`, and the footer shows only "Prague". The only measurable fault is the transient dusk dip (below).

## Round 1 items — verification

| # | Item | Status |
|---|---|---|
| 1 | Bold move earns its place | **Done.** Bands are 72vh; morning and day differ visibly; each band has a booking link; the Day photo is high-key; the Morning photo is cropped to the rain head and lightened. Per-tier prices are excluded by ruling. |
| 2 | Contrast | **Done, with an accepted residual.** Inactive rail links are now about 5–6:1 on light and use the bone-muted token on dark. Mobile final headline: worst sample 10:1. Dusk dip: see below. |
| 3 | Photo artifacts and repeats | **Done.** `hero-1` is removed. Evening uses `relax-empty-2`, Night `night-candle-2`, final band `final-empty-1`, and the shower smear is cropped out. |
| 4 | Closing headline innuendo | **Done.** "Book the whole spa for two" / "Free slots are in the calendar, day and night." |
| 5 | Heading formula | **Done.** |
| 6 | WhatsApp float collisions | **Done** (`.is-tucked` via IntersectionObserver). |
| 7 | Unconfirmed copy | **Done.** Photo-derived premises claims and payment assumptions are gone; "confirmed when you book" throughout; tier names are consistent. |
| 8 | Paper trail | **Done.** `TODO-OWNER.md` exists; email links go to `#email-TODO`; no district; CS switch and legal links flagged. |
| 9 | Sun disc | **Done** (deleted). |
| 10 | Small craft | **Done.** Price note is 17 px at 390; footer row on a baseline; the final photo fades to night; header gift link hidden over the hero; H1 clears the man's back by ~55 px. |

**Dusk dip, judged.** The 1440 sweep measured the dip as the 3vh light→dusk ramp crosses the sticky rail:
- Each rail line falls below 3:1 for 4–5 samples, about 24–30 px of scroll, with a worst sample of ~1.5:1.
- Each line falls below 4.5:1 for about 12–13 samples (~75 px).
- The aside price lines stay above 2.8:1 throughout.

It is a moving horizon crossing a line, not text parked on an unreadable tone. You can't be reading a line during the quarter-second the edge passes behind it, and it settles to ≥5:1 on both sides. A backing plate or a hard edge would remove the dip but also the move. I accept it as a residual and don't count it as a defect. Mention it in the port's accessibility notes so a later audit doesn't flag it blind.

## Hard fails

None. Checked:
- House-style list: no mono labels, eyebrows, decorative numbering, bordered boxes, stamps, tickets or outlined digits.
- No placeholder visible as brackets.
- The first mobile viewport is complete.
- Reduced motion is complete.
- No invented reviews, ratings, stats, hours or prices; only SAMPLE "from 1 990 Kč / 2 hours for two" is shown.
- Nothing sexualized. The new closing line is literal.

## Compared with the style reference (1440 hero)

| Aspect | Reference (Forestis / Trudon fold) | Variant | Note |
|---|---|---|---|
| Image coverage | 100% / 96% | 100% | ✓ |
| Elements in fold | 6 / ~12 | 10 (header gift link now hidden over the hero) | justified by the offer stack |
| Headline | light sans centred / Garamond caps + italic, bottom-left | Garamond caps + italic, bottom-left, clears the subjects | ✓ Trudon pairing |
| Below-fold rhythm | image group → short head → 2–3 lines → air | same; italic line kept only where it earns it | ✓ |
| Photo grade | blue-black shadows, single warm source | same, except the deliberate high-key Day band | see punch 1 |

## Punch list (polish; none blocks SHIP)

1. **Day sauna reads as a different room**: Day band, `media/day-sauna-2.jpg`. It is a bright pine showroom cabin with a different door and heater from the dark aspen `sauna-2` in the grid, so a guest sees two saunas. Regenerate slot `day-sauna` with `sauna-2.jpg` as the reference image. Prompt fix: "the same sauna as the reference: same aspen benches, same black door frame, same heater, now lit by bright even warm-white light from the concealed strip, high-key, no candles".
2. **Final band photo**: `.final`, `media/final-empty-1.jpg`.
   - Desktop: two blurred pale ovals in the mirror just above the candle row (viewport x≈1180–1300, y≈330–370). After the hero-1 ghost, they can read as reflected heads. Either `final-empty-2` has a cleaner mirror, or regenerate with "mirror shows only candle flames and steam, no rounded pale shapes".
   - Mobile: the crop is mostly out-of-focus mirror. Set `object-position: 62% 70%` at ≤760 px so the candle ledge and water are in frame under the headline.
3. **The prices italic line promises four numbers the page doesn't show**: `#prices`. "Four times of day, four prices." Within the ruling, change it to "Each time of day has its own price. Pick the light you like."
4. **Widows**:
   - 1440 voucher body: "buy." sits alone on its own line.
   - 390 prices italic: "four / prices." breaks mid-thought.
   - Add `text-wrap: pretty` to body paragraphs and `text-wrap: balance` to `.lede`.
5. **Add-on lines are vague**: `#addons`. "Something to toast with / Something light to share" is honest but sells nothing. Keep it for the prototype; when the owner confirms what's included (TODO-OWNER row exists), replace with concrete contents.
6. **Morning crop resolution**: `.band[data-tier="morning"] img`. Scale 2 on a 928 px source leaves ~464 source px for a 352 px box, which is soft on 2× screens. Acceptable for a temporary image. When real photos arrive, supply ≥1400 px for this slot.
7. **Housekeeping**:
    - The photo table in `TODO-OWNER.md` lists `media/temp/...` paths, but `index.html` loads the variant-local copies in `prototype/b-bold/media/`. Align the paths.
    - Delete the stray `media/TEMP-MEDIA copy.md` and `media/manifest copy.json`.
    - There is a `.git` directory inside `prototype/b-bold/`. Confirm it's intended before the port.
8. **Port note**: record the dusk-blend contrast residual and the four tier tokens plus `--color-dusk`, `--dusk-at` and `--evening-at` in the port's `@theme`. Swap the eager 2–3 MB JPGs for `next/image` with lazy loading below the fold.

## What works (keep it)

- The 390 first viewport: complete offer stack over the dark water, headline in the steam, and it still looks like Forestis.
- The day as four lights. The cool→warm→horizon→candle-brown→blue-black progression is done in CSS gradients, so it works with reduced motion and without JS. The bone 10vw "EVENING" over the amber horizon is the page's signature.
- One booking link per band plus the sticky aside: the bold move now converts instead of only decorating.
- Empty rooms in the bands and the final band: the page now shows a couple exactly twice (hero, relax room), which suits "the whole space, just for you".
- The quiet section rhythm after removing the italic sublines: plain hairline add-on list, real 4-step how-it-works, centred occasions line, borderless FAQ.
- An honest paper trail: `TODO-OWNER.md` covers every placeholder, and the copy says "confirmed when you book" instead of inventing terms.
