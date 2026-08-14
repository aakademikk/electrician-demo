# Implementation Plan: Electrician Demo Site

**Status:** Active
**Repo:** aakademikk/electrician-demo
**Deploy target:** Vercel (static, no build step)
**Purpose:** Re-brandable single-page demo site for an electrician. Sales weapon for Atwood Systems' AI receptionist pitch — "I built what yours would look like."

## Deliverable

- `/home/col/electrician-demo/index.html` — single self-contained HTML file (inline CSS + JS, no build step, no external deps, system font stack).
- `/home/col/electrician-demo/assets/` — 5 images referenced as relative `assets/<filename>`.

## Design system (Atwood brand)

- Canvas: `#090909`, deep `#050505`, panels `#101010` / `#141414` / `#181818`
- Greens: primary `#26e884`, secondary `#7bf06a`, accent `#0fd6b4`, support `#0b9e63`
- Text: ink `#f5f5f5`, muted `#b8bcc5`, faint `#7c818c`
- Headline gradient: `#7bf06a → #26e884 → #0fd6b4`
- Glass cards, hairline green edge-light, slow motion, luxe ease `cubic-bezier(0.22,1,0.36,1)`
- UK English, benefits-led, no lorem ipsum, no em-dashes, no hype words

## Phases

### Phase 1 — Scaffold
- [x] Create `/home/col/electrician-demo/` with `assets/`
- [x] Copy the 5 source images into `assets/`
- [x] `git init`, branch `main`, local identity set

### Phase 2 — Build `index.html`
- [ ] Head: title, meta description, OG tags, theme-color, inline SVG favicon, re-brand comment block
- [ ] Sticky glass nav: placeholder name, section links, phone + WhatsApp CTA, mobile burger
- [ ] Hero: full-width `electrician_hero1.jpg` bg, gradient headline, AI-receptionist sub-line, 2 CTAs, trust chips
- [ ] Instant-quote calculator (3 steps, state machine): job type radios → postcode + urgency → price range + "Book the slot" (scrolls to survey form, pre-fills job type + postcode). Phone mockup `electrician_quote_ui.jpg` beside it on desktop
- [ ] Services grid: 6 cards, inline SVG icons
- [ ] AI receptionist section: missed-call loop copy + `missed_call_dashboard.jpg`
- [ ] Coverage areas: replaceable placeholders ("Your town", "Nearby town 1"...) clearly marked
- [ ] Gallery: `electrician_hero2.jpg` + `electrician_hero_v2.jpg` as "recent work"
- [ ] Reviews: 3 five-star cards, realistic placeholder copy
- [ ] Free survey form: name, phone, job-type dropdown, postcode, message → inline success state (client-side only)
- [ ] Footer: placeholder phone/email/WhatsApp, "Demo site by Atwood Systems"
- [ ] JS: nav toggle, calculator state machine, form success state, scroll-reveal (respects reduced motion)

### Phase 3 — Verify
- [ ] Serve statically, confirm all 5 `assets/<filename>` resolve (HTTP 200)
- [ ] Confirm no external requests (no fonts, no CDN, no analytics in this build)
- [ ] Confirm calculator produces a price for all 6 job types
- [ ] Confirm form success state shows without a backend
- [ ] HTML validity spot-check (balanced tags, no broken refs)

### Phase 4 — Ship
- [ ] Commit plan + build to `main`, push to `aakademikk/electrician-demo`
- [ ] Report: paths, asset list, deviations, verification results

## Acceptance criteria

- Opens as a static file on Vercel with zero build step
- Mobile-first, sharp on a phone in WhatsApp browser
- All interactions client-side
- Every word benefits-led and electrician-specific
- All 5 images resolve relative to the page
