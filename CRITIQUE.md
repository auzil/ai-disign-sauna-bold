# Critique — b-bold — round 1

Verdict: FIX
Scores: Sells 4 · Fidelity 4 · Distinctiveness 3 · Typography 3 · Imagery 3 · Mobile 4 · Craft 3  (total 24/35)

Evidence per axis:
- **Sells 4**: the 390×844 fold has what (whole spa for two, Prague), the SAMPLE from-price, reassurance (24/7, robes included, 18+) and two Book a slot buttons. But the price section, a third of the page (4 919 of 15 046 px at 1440, 4 239 of 12 702 px at 390), carries one number and no action inside the bands.
- **Fidelity 4**: bone `#F2F1EB` page, 1080 px two-column mixed-ratio grid, ~200 px air, radius 0, dark single-source photos. All Forestis. The departures (11 fold elements against Forestis' 6, Garamond caps instead of light sans) are allowed by the brief.
- **Distinctiveness 3**: the day→evening blend is the best moment on the page. Morning (`#E2E5E3`) and Day (`#F7F2E7`) read as the same pale section, though, both band photos are night-lit, and the scrubbed sun disc is invisible on light bands. The move only lands in its second half.
- **Typography 3**: the hero is strong and the 10vw tier names have real presence. Every section repeats the same caps H2 + italic line + centred paragraph (7 times), inactive rail links fail contrast, and the final band's italic line breaks badly ("their / prices").
- **Imagery 3**: consistent candle-dark grade, tasteful, never sexualized. Problems: a ghost face in the hero-1 mirror, the couple-in-jacuzzi scene twice (hero and final), sauna, shower and relax (the same couple in the same pose) each twice, and band photos that don't match their hour.
- **Mobile 4**: readable, the sticky WhatsApp + Book bar works, and the band rail takes the band colour. The price section is long (4 screens with one fact), and the key price note is set at 14 px.
- **Craft 3**: reduced motion is complete and focus trap and Esc work. Measured contrast fails, the floating button collides with content, `TODO-OWNER.md` is missing, and the sun is an invisible soft-light layer that still costs paint.

## Hard fails

None that block on their own. Checked:
- House style: no mono labels, eyebrows, decorative numbering (1–4 in How it works is a real sequence), borders, stamps, tickets or outlined digits. Serif caps + italic line is Trudon's pairing and isn't on the banned list, but it's used as a formula in every section (punch item 5).
- First mobile viewport: price, reassurance and primary action are all present.
- Reduced motion: content is complete. The 1440 full-page capture with motion showed the final band without its photo. A viewport shot scrolled to `#book` shows the photo, so this is a capture timing issue with the 2752 px eager image, not a page bug.
- Invented facts: no reviews, ratings or stats, and no hours or tier prices beyond SAMPLE "from 1 990 Kč / 2 hours for two". There are softer inventions, though: premises details taken from the AI photos, assumed booking-system behaviour, and a specific district (punch items 7–8).
- Borderline: the final headline at 390 sits partly over a bare shoulder at 2.4:1 (punch item 2).

## Compared with the style reference (1440 hero)

| Aspect | Reference (Forestis fold / Trudon fold) | Variant | Fix |
|---|---|---|---|
| Image coverage | 100% (F), 96% (T) | 100% | keep |
| Elements in fold | 6 (F), ~12 (T) | 11 (menu, EN/CS, wordmark, Gift voucher, Book, H1, lede, price, CTA, gift link, facts) | acceptable, the offer stack is required; "Gift voucher" in the header and "Give it as a gift" in the hero repeat each other, so drop one on desktop |
| Headline | light sans ~2.9vw centred (F); Garamond caps ~2.8vw + italic line, bottom-left (T) | Garamond caps ~3.2vw, two lines, italic lede, bottom-left | good Trudon execution; second line ends ~30 px from the man's back, so allow at most 46rem width |
| Primary action | plain text "Book" (F); outlined caps button (T) | solid bone block, radius 0 | right call for conversion |
| Below-fold heads | light sans sentence case, no subline (F) | caps + italic line in all 7 sections | see punch item 5 |
| Photo light | blue-black shadows, one warm source (F); flame reflections in brass and mirror (T) | matches both | keep |
| Bold move | n/a: Forestis is all bone + photo | four full-bleed bands Morning→Night | lands at dusk, flat in the first half (punch item 1) |

## Punch list (most important first, max 10)

1. **Make the bold move earn its third of the page**: `#prices`, `.band`.
   - Cut each band's `min-height: 100vh` to ~72vh on desktop. At 390, switch `.band__photo` from 4:5 to 3:2 so a band fits one screen with its text.
   - Make Morning visibly different from Day: shift `--color-morning` to a cool blue-grey such as `#D9E0E3` and keep Day warm, or nobody sees "morning" before "day".
   - Give every band a conversion job without inventing numbers. Under each italic line, add a text link to `#booking-TODO`: "Book a morning slot", "Book a daytime slot" and so on. Reserve a price line in the band text column in the aside price style (`2rem` Garamond), and ask the owner for SAMPLE per-tier prices so it can be filled. Until then, leave it out; don't show a dash or "—".
   - Regenerate the Day photo so it isn't another night frame: regenerate slot `sauna`, prompt fix: "even, bright warm-white light from a concealed ceiling strip, high-key, pale aspen, no candles, no visible windows". Morning `shower-2` can stay, but grade it lighter: `filter: brightness(1.08) saturate(.9)` on the Morning band only.
2. **Contrast in and around the bold move**: `.rail a`, `.day__body` gradients, `.final`.
   - Inactive rail links measure 2.1:1 on the Day cream and 1.8:1 on the dusk mid-tone, and they're working anchor links. Make the inactive state `--color-ink-soft` (`#5E5B55`, ~6:1) on light and `rgb(242 241 235 / .74)` on dark instead of the opacity fade.
   - Desktop: the day→evening blend leaves a span where both ink and bone measure ~3.2–3.5:1, and the sticky rail passes through it. Shorten the dusk stop in `.band[data-tier="evening"]` to the first ~10vh of the band. Flip the rail tone at the gradient's midpoint, not at the "24% into the band" offset.
   - 390: "TONIGHT IS A GOOD" in `.final` sits over the man's shoulder at 2.4:1. Set `.final__media img { object-position: 85% 40% }` on mobile and raise the bottom shade so it reaches `--color-shade` by 55% height. Target ≥3:1 under every glyph.
3. **Photo artifacts and repeats**.
   - Regenerate slot `hero` image `hero-1.jpg`: a blurred extra face appears in the mirror between the couple. It reads as a third person, the opposite of "nobody else inside". Prompt fix: "mirror shows only steam and candle reflections, no faces or figures reflected". Better still, don't use a couple shot for `.final` at all: hero and final are the same scene. Use a people-free wide frame instead (regenerate `water` at 16:9: "wide view of the empty candle-lit stone jacuzzi, steam, brass spout, no people").
   - `relax-1` (Evening band) and `relax-2` (relax room) show the same couple in the same robes and pose. Swap the Evening band to `robes-2` or regenerate slot `relax`: "empty lamp-lit relax room, two loungers, folded throw, candle, no people".
   - `sauna-1`/`sauna-2` and `shower-1`/`shower-2` also repeat. The Day fix in item 1 resolves sauna. For shower, use `shower-1` in the space grid only, and the regraded `shower-2` in Morning only if its crop differs clearly (tight on the rain head).
   - Minor: `shower-2` has a dark scribble-like smear on the misted glass (right third). Crop it out with `object-position: 30% 50%`.
4. **Innuendo in the closing headline**: `.final h2`. "Tonight is a good night for it" in caps over a bare-shouldered couple reads as a double meaning, and intake §7 bans innuendo. Replace it with something literal, for example "A WHOLE SPA, TONIGHT OR ANY NIGHT" with the italic line "Free slots and prices are in the calendar." Set the lede `max-width` to ~26rem so it doesn't break after "their".
5. **Stop the heading formula**: `.intro`, `.space`, `.addons`, `.how`, `.voucher`, `.faq`. Seven sections repeat caps H2 + italic serif line + centred paragraph. Trudon uses the italic line once, and Forestis has none. Keep the italic line on the hero, `#prices` and `#voucher` only. Delete it in intro, space, addons, how and faq; the body text already says it. That restores Forestis' quietness and keeps the pairing from turning into a tic.
6. **WhatsApp float collides**: `.wa`, desktop. At 1440 it sits on the bottom-right corner of the Morning and Evening band photos. When the intro facts row scrolls to the bottom of the viewport it overlaps "Adults only" (x 1005–1260 against 1233–1365), and it sits over the footer columns. Add an IntersectionObserver that toggles a class to hide `.wa` while `.day__body`, `.final` or `footer` intersect the viewport. The aside and the final band already offer Book and WhatsApp there.
7. **Copy states things nobody confirmed**: intro, space, addons, FAQ.
   - Premises details come from the AI photos, not the intake: "rain shower", "by candlelight", "Two low loungers, linen, a candle and a glass of water", "Chilled, with two glasses, ready by the jacuzzi", "Fresh seasonal fruit". Rewrite them neutrally ("shower", "a quiet room to rest", "Prosecco", "Fruit plate") or flag each one.
   - Booking-system behaviour is assumed: "shown before you pay" (payment method TODO); "the amount and the maximum number of guests are shown in the calendar" and the cancellation line (calendar set-up TODO). Soften to "confirmed when you book" and list these in TODO-OWNER.
   - Naming: intro says "Morning, afternoon, evening and night" but the tier is "Day". Use the tier names.
8. **Placeholders need their paper trail**: there is no `TODO-OWNER.md` in `b-bold/`; `a-close` has one. Create it, listing every `data-placeholder` plus the copy items from 7. In the menu, `mailto:hello@lumenspa.cz` (line ~807) has no `data-placeholder`. `lumenspa.cz` may be someone else's real domain, so point both mailto links to `#email-TODO` and keep the sample text visible. "Vinohrady, Prague 2" is a specific location the owner never gave. Keep it only if it's listed as SAMPLE in TODO-OWNER; otherwise show "Prague" plus "Open in maps". The EN/CS switch is visual only, which is fine for the prototype: leave EN as the current state, but make sure `#lang-cs-TODO` is in TODO-OWNER.
9. **Sun disc: show it or cut it**: `.sun`. A 70vmax radial layer with `mix-blend-mode: soft-light` is scrubbed across the whole section, but it's invisible on Morning and Day and barely visible on Night. It costs a full-viewport blend repaint on every scroll frame on phones for no visible return. Either remove `mix-blend-mode`, use a normal-blend warm radial (`--color-flame` at .18 on light bands, .35 on dark) and limit it to `min-width: 901px`, or delete it. The colour bands are the move; the disc is optional.
10. **Small craft**:
    - The price note in `#prices` ("Morning, day, evening and night each have their own price…") is 14 px at 390. It's a sell sentence, so set it to `--text-body` (≥16 px).
    - The footer line "Photos on this page are temporary illustrations." sits ~5 px above the baseline of Terms/Privacy. Align with `align-items: baseline`.
    - The `.final` photo ends in a visible hard edge above the footer. Extend the bottom gradient to full `--color-night` at 100%.

## What works (keep it)

- The 390 first viewport: steam above for the headline, the couple and candles in the middle, the price/CTA/facts stack over dark water. It sells and still looks like Forestis.
- The evening→night stretch of the bands: the amber-to-candle-brown blend under the 10vw "EVENING" in bone is the page's memorable moment. Protect it while fixing the first half.
- The mobile tier rail taking the band colour, and the sticky WhatsApp + Book bar after the hero.
- The CSS-gradient core of the bold move: it works with reduced motion, without JS and in full-page captures.
- The Forestis space grid (1080 px, 20 px gutter, mixed ratios) and the radius-0, borderless discipline everywhere.
- Add-ons as a plain hairline list on night and How it works as a real 4-step sequence: no icon tiles, no cards.
- No reviews, ratings or stats anywhere. FAQ and How it works carry the reassurance honestly.
