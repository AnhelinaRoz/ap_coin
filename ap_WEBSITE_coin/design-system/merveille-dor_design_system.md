# Merveille d'Or — Design System

Extracted from `merveille-dor.html` + `merveille-dor-brand-guidelines.pdf`.
Source of truth for any UI built for this brand.

---

## 1. Brand Essence

- **Name**: Merveille d'Or — legal entity Merveille d'Or SA
- **Descriptor**: Négociant en métaux précieux — Genève, Suisse
- **Positioning**: Swiss private-bank discretion × assay-laboratory rigour. "We don't sell a promise — we hand over matter."
- **Tone verbs**: weighed, verified, sealed, traced, handed over. Never "powerful", never "seamless".
- **Languages**: FR (default), EN, DE, IT — full parity, no partial translations.

## 2. Color Palette

Ten tokens. Nothing else. Shading tones inside the 3D coin texture are exempt.

| Token | Value | Usage |
|---|---|---|
| `--navy` | `#0B1F3A` | Primary dark ground, body background |
| `--navy-deep` | `#071626` | Footer, hero gradient tail, mobile drawer |
| `--navy-soft` | `#12274A` | Lifted dark surfaces |
| `--gold` | `#C6A15B` | Primary accent, marks, rules, active states |
| `--gold-bright` | `#E4C98B` | Accent on dark — primary CTAs, highlights |
| `--gold-dim` | `#9C7C42` | Accent on light — eyebrow labels, captions |
| `--cream` | `#F6F1E7` | Light ground, primary text on dark |
| `--cream-dim` | `#EAE2D2` | Secondary text on dark |
| `--line` | `rgba(198,161,91,.32)` | Hairline rules & borders |
| `--line-soft` | `rgba(198,161,91,.16)` | Subtle dividers, grid gaps |

Rules:
- Line / Line Soft are **hairlines only** — never fills.
- Dark bands alternate with cream bands; a page rhythm is dark hero → light maison → dark services → light valeurs → dark contact → deep footer.
- `::selection` is gold background on navy text.

## 3. Typography

Two faces only.

**Playfair Display** (serif display) — weights 500, 600, 700, 900 + 500 italic.
Fallbacks: Georgia (body), Didot / "Times New Roman" / Georgia (wordmark).

**Montserrat** (sans UI) — weights 300, 400, 500, 600.
Fallbacks: "Helvetica Neue", Arial, sans-serif.

| Element | Face / Weight | Size | Tracking | Case |
|---|---|---|---|---|
| Wordmark "MERVEILLE DOR" | Playfair 700 | 52px | 9px | UPPERCASE |
| Strapline "MAISON D'OR · GENÈVE" | Montserrat 400 | 15px | 6.5px | UPPERCASE |
| Nav wordmark | Playfair 700 | 14px | .22em | UPPERCASE |
| Eyebrow label | Montserrat 500 | 11px | .32em | UPPERCASE |
| Hero tagline | Playfair 500 italic | 18–24px fluid | normal | Sentence |
| Section H2 | Playfair 700 | 34–60px fluid | -.01em | Sentence |
| Values H3 | Playfair 500 italic | 24–34px fluid | normal | Sentence |
| Service H3 | Playfair 700 | 30–44px fluid | -.01em | Sentence |
| Figure number ("999.9") | Playfair 600 | 24–32px fluid | normal | As written |
| Figure label | Montserrat 300 | 10px | .16em | UPPERCASE |
| Nav link / CTA / button | Montserrat 500 | 11–12px | .24–.26em | UPPERCASE |
| Body copy | Montserrat 300 | 14.5–17px fluid | normal | Sentence |
| Form label | Montserrat 300 | 10px | .2em | UPPERCASE |
| Footer legal | Montserrat 300 | 10px | .08em | Sentence |

Fluid sizing uses `clamp()` — e.g. H2 `clamp(34px,4.6vw,60px)`.

## 4. Logo Suite

**Mark** (viewBox 0 0 200 200): double-outline lozenge (outer stroke 4, inner 1.6) containing a solid 16-point compass star, center dot r=5.5 in the contrast color. Inline on the live site at heavier strokes (outer 5 / inner 2), 30×30 header / 26×26 footer.

**Eyebrow mark**: single-outline diamond only (stroke 8, no star, no dot) at 9×9px.

**Lockups** (viewBox 0 0 760 220): primary (gold mark, navy wordmark), reversed (navy fill, gold mark, cream wordmark), all-gold, all-navy. Wordmark inside lockups reads MERVEILLE DOR **without apostrophe**; everywhere else the name keeps the apostrophe.

## 5. Spacing & Layout

- Container: `max-width:1360px`, padding `clamp(20px,5vw,72px)`.
- Section bands: `padding: clamp(110px,16vw,190px) 0`.
- Grids: maison `.9fr / 1.1fr` two-column; services 2-up with 1px `line-soft` gaps; valeurs list rows `1.1fr / 2fr` with hairline top borders; contact 2-column.
- **Zero border-radius everywhere** (`border-radius:1px` max on buttons). Sharp, architectural corners.
- Separation by hairline rules and whitespace, never cards-in-cards or shadows.

## 6. Components

**Eyebrow** — 9px diamond mark + uppercase tracked label, gold on dark / gold-dim on light.

**Nav** — fixed, transparent → on scroll: reduced padding, `rgba(7,22,38,.78)` + `blur(14px) saturate(140%)`, `line-soft` bottom border. Links 11px uppercase with underline growing left→right (`right:100%→0`). CTA: 1px `line` border, hover inverts to solid gold/navy. Mobile: burger → full-screen navy-deep drawer with 32px Playfair links.

**Buttons / CTAs** — text-link style: uppercase tracked label, permanent hairline baseline, gold line growing in on hover. Service CTA has a 24px dash that extends to 38px on hover. All CTAs are **magnetic** (translate toward cursor, 0.28×/0.5× factors, `.25s ease-soft` return).

**Forms** — transparent fields, bottom hairline only, gold focus border. Label 10px uppercase gold-dim. Submit = bordered gold button that inverts on hover.

**Figures** — Playfair 600 number over 10px uppercase gold-dim label, separated by a top hairline.

## 7. Motion System

Tokens:
- `--ease: cubic-bezier(.16,.8,.24,1)` — primary
- `--ease-soft: cubic-bezier(.22,.61,.36,1)` — hovers, underline growth
- `--dur-s: 420ms` / `--dur-m: 900ms` / `--dur-l: 1400ms`

Patterns:
- **Scroll reveal**: `opacity 0→1`, `translateY(38px)→0`, `clip-path inset(0 0 12% 0)→0`, 900ms ease, staggered 80ms steps (`.d1`–`.d4`), IntersectionObserver threshold .16, once-only.
- **Hero entrance**: staged — coin glow, coin scale-in, lockup lines, tagline, CTAs, scroll cue; each on its own delay.
- **Magnetic hover**: CTAs drift toward pointer, spring back on leave.
- **Scroll cue**: gold segment sweeping a 38px hairline, 2.6s infinite.
- **Hero parallax**: body translates at 0.18×scroll and fades; coin stage at 0.08×.
- **`prefers-reduced-motion`**: all animations collapse to .01ms; auto-spin drops to near-zero.

### 7.1 The Coin (signature interaction)

Three.js WebGL coin, right half of hero:
- Geometry: cylinder extrude r=1, depth .16, bevel .05/.045, 160 curve segments.
- Faces: 1024px canvas texture — radial gold gradient, guilloche rings, double rim, arc lettering "MERVEILLE D'OR · GENÈVE · SUISSE · 999.9", engraved brand rosette (dark offset + light offset + core tone passes). Matching bump map. Edge: reeded 256×64 canvas, 24× repeat.
- Material: `MeshPhysicalMaterial`, metalness 1, roughness .28, clearcoat .35, ACES tone mapping, RoomEnvironment PMREM + key/rim/fill lights.
- Behavior: continuous slow auto-spin; pointer hover adds position-follow offset; **drag adds velocity with 0.90 friction** (inertial spin); idle after 1.1s blends back to autonomous mode; gentle sine bob.
- Readout: "AXE 000°" tabular-numeric rotation display + drag hint, shown on first interaction.
- Fallback: if WebGL/module load fails, a CSS 3D coin (two SVG faces, `rotateY` keyframes, conic-gradient sheen) takes over.

## 8. Iconography & Texture

- Icons are inline SVG, 1px-class strokes, gold; no icon fonts, no emoji.
- Film grain overlay on hero: inline SVG `feTurbulence`, opacity .05, `mix-blend-mode: overlay`.
- Radial gold glows behind the coin (14%/8% opacity), never purple or blue gradient washes.

## 9. Accessibility & Baselines

- `:focus-visible` — 1px gold-bright outline, 4px offset.
- Semantic landmarks, `aria-expanded` on burger, `role="group"` on language switch.
- Mobile breakpoint 980px: single columns, centered coin at .85 opacity, burger nav.

## 10. Content / Verbal Identity

- Hero tagline: FR «L'or physique, entre vos mains.» / EN "Physical gold, in your hands." / DE / IT.
- Signature figures: 999.9 fineness · 24h traceability · GE Geneva.
- Values triad: Précision · Discrétion · Provenance.
- Services: Acheter (Composer une position) · Vendre (Demander une évaluation) · Conserver (dépôt sécurisé).
- Contact: Genève — sur rendez-vous · contact@merveilledor.ch · Lun–Ven 09h–18h.
- Legal: © 2026 Merveille d'Or SA — Genève.
