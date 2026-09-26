# Merveille d'Or — Implementation-Ready UI Design Prompt

> Composed per the design-system-builder workflow: design system (merveille-dor_design_system.md) × PRD (prd.md). Hand this prompt to any UI engineer/agent to reproduce the experience.

---

## Aesthetic Principles
- Luxury through **precision, restraint, material quality, typography, spacing and motion** — never through decorative gold.
- Sharp architectural corners (radius ≤ 1px). Hairline rules instead of cards and shadows.
- Dark navy ↔ cream band rhythm. One accent family: gold.
- Very little copy; hierarchy carried by Playfair Display scale and Montserrat tracking.
- Every animation is intentional and physically believable; every element has a reason to move.

## Required Tokens (exact)
```
--navy:#0B1F3A; --navy-deep:#071626; --navy-soft:#12274A;
--gold:#C6A15B; --gold-bright:#E4C98B; --gold-dim:#9C7C42;
--cream:#F6F1E7; --cream-dim:#EAE2D2;
--line:rgba(198,161,91,.32); --line-soft:rgba(198,161,91,.16);
--ease:cubic-bezier(.16,.8,.24,1); --ease-soft:cubic-bezier(.22,.61,.36,1);
--dur-s:420ms; --dur-m:900ms; --dur-l:1400ms;
```
Fonts: Playfair Display (500/600/700/900 + 500i), Montserrat (300/400/500/600). Type scale per the design-system table (fluid `clamp()` sizes).

## Brand Assets
Use ONLY the attached MDR SVG lockups/marks (double-outline lozenge + 16-point compass star + contrast center dot). Do not redraw or restyle. Inline usage: 30×30 header (strokes 5/2), 26×26 footer, 9×9 single-diamond eyebrow mark. Lockup wordmark = "MERVEILLE DOR" (no apostrophe); running copy = "Merveille d'Or".

## Hero (signature)
- Full-viewport navy scene: radial gold glows, film grain (SVG feTurbulence, .05 overlay), no black first frame.
- Logo lockup + tagline («L'or physique, entre vos mains.») + three text-link actions (Acheter / Vendre / Nous contacter) + scroll cue with sweeping gold segment.
- **3D coin** (Three.js, right half):
  - Extruded cylinder r=1 d=.16, bevel .05/.045, 160 segments; 1024px canvas face texture (radial gold gradient, guilloche rings, double rim, arc lettering "MERVEILLE D'OR · GENÈVE · SUISSE · 999.9", engraved rosette in 3 offset passes) + bump map + reeded edge texture (24× repeat).
  - MeshPhysicalMaterial metalness 1 / roughness .28 / clearcoat .35; ACES tone mapping; RoomEnvironment PMREM + warm key / cool rim / gold fill lights.
  - Motion: slow auto-spin; horizontal pointer velocity adds rotational velocity, friction .90; idle >1.1s blends to autonomous; vertical pointer → tilt ±.16 rad; sine bob .05; degree readout + drag hint after first interaction.
  - Entrance: scale 1.15→1 + exposure ramp over ~1.4s.
  - Touch = drag. `prefers-reduced-motion` → near-static.
- Hero parallax on scroll: body 0.18× + fade, coin stage 0.08×, camera pull-back.

## Rest of Page (motion continues, coin does not)
- **La Maison** (cream): eyebrow + H2 2-col grid; copy reveals staggered 80ms; figures 999.9/24h/GE count up over a top hairline that draws in.
- **Acheter / Vendre** (dark, 2 panels split by 1px line-soft): hover spotlight follows cursor (radial gold .10), ghost Roman numerals I/II, CTA dash 24→38px.
- **Valeurs** (cream): hairline-row list; italic Playfair titles; rows reveal with clip-path; title tracking expands on hover.
- **Contact** (dark): 2-col; underline-only form, gold focus; submit inverts.
- **Footer** (navy-deep): mark + wordmark, links, legal.
- Section entrances: clip-path mask + translateY + scale .98→1, 900ms `--ease`, staggered; once-only via IntersectionObserver.
- Magnetic CTAs site-wide (hover-capable pointers only).

## i18n
FR default, EN/DE/IT complete dictionaries, `data-i18n` keys, `documentElement.lang` switch, active-state language switcher in nav + drawer.

## Baselines
- `:focus-visible` gold outline; semantic landmarks; aria on burger/switch.
- Breakpoint 980px: single column, coin centered .85 opacity, burger → full navy-deep drawer (Playfair 32px links).
- Selection = gold on navy. No external images; all texture code-drawn (SVG/canvas/WebGL). Contact form = front-end demo only.
- Graceful fallback: if WebGL/module fails, CSS 3D coin (two faces + conic sheen, rotateY keyframes) replaces it.
