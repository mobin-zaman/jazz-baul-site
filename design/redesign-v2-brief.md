# Jazz Baul Site Redesign — Research Brief (v2)

## Solo-artist site design conventions (synthesized from earlier web research: scrile, splice, bandzoogle, colorlib, plus alexamen.com reference)
- **Homepage job for a solo artist = identity + direct audience capture.** Above the fold: name, sound sample (embeds), one primary CTA (listen/follow), then proof. Structure is lean: hero → music → about → shows → contact → social.
- **One dominant goal.** Don't bury the primary action; four actions in order: listen, contact, subscribe, buy.
- **Modern/premium feel** comes from: generous whitespace, oversized display typography (tight leading, negative tracking), a single strong color/theme system (monochrome reads "editorial/premium"), bold editorial images, and real motion on entrance (stagger) + button press feedback.
- **Dark aesthetic** is the norm for indie/fusion artists; a **light theme toggle** broadens accessibility and is now best practice (see theme research).
- **Monochrome (black & white)** design: near-black bg + near-white text, one muted accent (can be a single accent color used very sparingly), grayscale imagery, hairline borders. High contrast. This is the current "premium editorial" language.

## Content to include (from real browsing of Akram's socials — all real facts)
### Identity
- **Akram Siddiquee** (artist: Jazz Baul) — Singer, Songwriter, Musician, Producer. YouTube: @JazzBaul (342 subs, 28 videos, "Singer, Songwriter, Musician, Producer"). Facebook: jazzbaaul. Linktree: linktr.ee/Jazzbaul.
- Owner of **Jazz Baul Records**. Based Dhaka (Mirpur), Bangladesh. Journey since 2018. Works with Song Zone and BackStage Club; past Jatra Biroti + Celtron (digital agency); studied North South University.
- Baul (Bengali mystic folk) × Jazz fusion, bilingual Bengali+English.

### Discography (YouTube tracks — real IDs)
Official/titled songs:
1. **I'll See You In My Dreams | স্বপ্নদর্শীর চোখে তুমি** — DOAXEQ11MUA (Jazz Baul Records, feat. @Daruchinib9) — flagship
2. **Oronne Boishakh | অরণ্যে বৈশাখ** — MFEuVLQWdIo
3. **AAY RE AAY | আয় রে আয়** — mSXWIlz2Q00
4. **The Painter** — oE-uEaeuSBs
Live recordings / sessions:
5. **"Far away from you"** (live) — RuPXIZNzBDw
6. **live vocal** (liverecording) — QKuSMzjg78o
7. **jamming** (guitar live) — xf8C_0db1hs
(Excluded: political/cat parody 7aKCHsQh88o, DIY-beats producer posts, personal shorts.)

### Social proof bits
- Golden-hour beach photo with guitar (the site's portrait image) — "wanderer with instrument" fits the Baul mystic identity.

## YouTube embed approach (research-informed)
- Use standard YouTube iframe embeds: `https://www.youtube-nocookie.com/embed/{VIDEO_ID}` (privacy-enhanced; e.g. `youtube-nocookie.com` is the recommended no-cookie endpoint).
- **Responsive:** wrap in `.video-wrap` with `aspect-ratio:16/9` (or 16/9 via padding-top) so it scales; width 100%.
- **Theming:** YouTube iframe is black chrome; on a dark site it blends. For a B&W/light toggle site it works as a "video player card" with border. Do NOT try to re-theme YouTube's internal player — frame it.
- **Lazy-load:** `loading="lazy"` on the iframe is limited; commonly defer by setting `src` on interaction, or rely on the section reveal. Keep simple: standard iframe + `loading="lazy"`.
- Confirmed titles/IDs via YouTube oEmbed (ground truth).

## Black & white theme-toggle (design note)
- Two palettes via CSS custom properties on `:root` / `[data-theme="light"]` (CSS variables swapped by a toggle button).
- Persist choice in `localStorage`; respect `prefers-color-scheme` on first visit.
- Mono accent: keep the existing single accent but desaturate to a neutral/graphite so the whole site is B&W; the toggle switches bg/text hue (deep near-black ↔ soft off-white) with **transition on colors** (not transform) for the theme flip.
- Theme flip is an infrequent action — eligible for a short cross-fade (state indication), ~200-300ms.

## Modern polish targets (find-animation-opportunities lens)
Existing site already has: reveals (IO+fallback), reduced-motion, hover gating, :active scale(.97), stagger, menu (opacity/transform). To feel MORE modern/premium in B&W:
- Discography/embed cards: entrance **stagger** on scroll (already pattern); add a subtle lift (`translateY(-3px)` + border-lighten) on hover for track rows.
- **Theme toggle**: not frequent → brief cross-fade on palette swap; button press scale.
- Track rows: hover reveals a thin accent rule/light; playing state (if any) not needed.
- Video cards: lazy fade-in when scrolled into view.
- Keep restraint — this is a brochure/music site, not a dashboard.

## Verified biographical facts (from Baul/fusion + footprint research — add to bio copy)
- **Akram Siddiquee, "aka Jazz Baul"** — founded **Jazz Baul Records** in Dhaka (Owner, Jan 2025); previously **Sr. Sound Designer at Riseup Labs**; 10+ years as sound designer / audio engineer / music producer (film foley, Dolby Atmos, Unilever animation sound design).
- Self-description: "singer songwriter, multi-instrumentalist, sound sculptor, founder of Jazz Baul Records".
- Instagram @akram_jazzbaul tagline: "Beats in the dark, rhythm comes alive. Jazz Baul Records is where the groove begins."
- Real session work: mixing credit on "Jontro Das — Keu Janena | Campfire Session S2 E17".
- Baul×Jazz is a real current genre position, not a cliché: Maqsoodul Haque on "Baul fusion is a massive music industry now"; Arnob's band "Bangla" blends Baul/Lalon with jazz & blues; Dhaka jazz fuses esraj/sarod/dhol/bansuri with sax/guitar.
- **Authenticity caution (reputational):** "asol baul" (real) vs "nakol baul" (pretender) is a contested category — position the artist as *drawing on* Baul tradition, NOT claiming a fakir lineage or guru transmission.
- Baul imagery available if wanted: uncut hair bun, saffron robe (alkhalla), ektara (one-string), tulsi beads, "Achin Pakhi" (unknown bird) metaphor, Lalon's "Maner Manush."

(Sources: Instagram @akram_jazzbaul; FB jazzbaaul; Fiverr akramsiddiquee; LinkedIn akramsiddiquee; SBS Bangla; Daily Star; The Criterion — see delegation report.)

## Decisions for the build (what changed from v1)
1. Add a **Discography** section with ALL tracks (embedded YouTube, B&W video cards) — replaces/expands the old 2-card Music section.
2. **Theme toggle button** in the nav: dark ↔ light, persisted, B&W throughout (desaturate the old accent).
3. Keep the golden-hour photo (now monochrome-filtered to match B&W).
4. Modern editorial B&W palette: `--bg` deep near-black ↔ `--bg` soft off-white; matching text/inverse; hairline borders; mono display + system body.
5. Keep: hero, about, shows (bookings), follow, email join-list, mobile menu, all animation quality.
6. "Listen" CTA → the discography embeds / linktree.