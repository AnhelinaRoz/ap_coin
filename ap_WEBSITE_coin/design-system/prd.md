# Merveille d'Or — Website PRD

## Elevator Pitch
A motion-first digital luxury object for Merveille d'Or (MDR), a newly established Geneva physical gold & precious metals dealer. Not a conventional luxury site — a cinematic opening scene built around a photoreal, physically manipulable 3D gold coin.

## Problem Statement
New Geneva gold dealers look interchangeable: black-and-gold templates, vault clichés, dashboard aesthetics. MDR needs a first impression that communicates Swiss precision, discretion and material truth in under three seconds — and feels hand-made by a high-end creative studio.

## Target Audience
Private clients (FR/EN/DE/IT) buying or selling physical gold and precious metals in Geneva — UHNW individuals, family offices, collectors. They value discretion, provenance and craft.

## USP
The coin. A true interactive 3D object — inertia, momentum, resistance, tilt — that the visitor physically manipulates with mouse or touch, then releases back into a slow autonomous rotation. One unforgettable signature, never repeated elsewhere on the page.

## Hard Constraints (from client brief)
1. **Logo**: attached MDR assets are the ONLY logo source — never redrawn, modified, or replaced.
2. **No black-screen start** — visually rich from frame one; initial state already animated.
3. **Coin**: realistic physical gold (reflections, relief, weight); mouse-driven with inertia/momentum/idle-return; subtle vertical tilt response; touch = drag; NOT a CSS spin, NOT a game.
4. **Don't overuse the coin** — hero only. After the hero, other motion concepts take over.
5. **Motion-first everywhere**: camera movement, depth transitions, layered parallax, typography choreography, masked reveals, magnetic buttons, scroll velocity. No gratuitous fade-ins; every element has a reason to move.
6. **Forbidden**: black-and-gold templates, golden threads, gold bars, vault/stock Geneva photos, crypto aesthetics, dashboards, glassmorphism, rounded cards, generic gradients.
7. **Typography**: brand faces only (Playfair Display / Montserrat), large, editorial, very little copy.
8. **Languages**: FR default + EN / DE / IT.
9. **Key actions always reachable**: Acheter · Vendre · Nous contacter — integrated elegantly, not generic CTA buttons.

## Scope (pages/sections)
Single-page experience:
1. Hero — logo lockup, tagline, interactive coin, three key actions, scroll cue.
2. La Maison — one idea: "Une matière, une discipline." + figures (999.9 / 24h / GE).
3. Acheter / Vendre — two-panel split, hover spotlight, dash CTAs.
4. Valeurs — Précision · Discrétion · Provenance hairline list.
5. Contact — private appointment info + minimal form.
6. Footer — mark, links, legal.

Deliberately no pricing, no product grid, no testimonials, no dashboard.

## UX/Interaction Notes
- Entrance choreography: staged (glow → coin resolve → lockup lines → tagline → actions → cue).
- Coin: continuous slow auto-spin; horizontal pointer velocity → rotational velocity with friction (≈0.90/frame); idle >1.1s blends back to autonomous; vertical pointer → ±0.16 rad tilt; rotation readout in degrees; drag hint on first move.
- Scroll: hero parallax (body 0.18×, coin 0.08×, fade), camera pull-back; sections enter via clip-path mask + translate + slight scale; hairlines draw; figures count up.
- Magnetic CTAs (0.28×/0.5× pull, spring return, hover-capable devices only).
- `prefers-reduced-motion`: all motion collapses; coin near-static.
- Mobile ≤980px: single column, centered coin behind text at reduced opacity, burger drawer.
- Form is a front-end demo (no backend) — submission confirms locally only.

## Success Criteria
- First frame already shows brand + lit, rotating coin.
- Coin manipulation feels physical (acceleration, deceleration, momentum).
- Page reads in <10 seconds of copy; hierarchy carried by type and motion.
- Indistinguishable from bespoke studio work; zero template signals.
