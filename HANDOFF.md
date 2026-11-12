# Sketchbook Wing (`ציפור המחברת`) — Project Handoff & Context

## 1. Project Overview
- **Concept:** A single-file, zero-dependency HTML5 Canvas web game inspired by a hand-drawn pencil sketch of a bird collecting coins across open notebook skies (no pipes/obstacles yet).
- **Target Audience:** Kids (Hebrew-speaking interface, RTL layout, playful notebook aesthetic).
- **Repository & Hosting:** Hosted on GitHub Pages at `https://github.com/EliShayGH/sketch-bird` (Live URL: `https://elishaygh.github.io/sketch-bird/`).
- **Architecture:** 100% self-contained inside a single `index.html` file (HTML, CSS, Canvas 2D vector procedural rendering, and Web Audio API sound synthesis). No external frameworks, build steps, or image assets required.

---

## 2. Core Gameplay Mechanics
- **Zero-Gravity Steady Altitude Flight:**
  - Unlike standard Flappy Bird, the bird **holds her current altitude** automatically when no vertical input is pressed.
  - **Up (`↑` / `W` / On-screen Up button):** Smoothly climbs upward.
  - **Down (`↓` / `S` / On-screen Down button):** Smoothly dives downward.
  - Clamped safely between top HUD clearance (`getCeilingY()`) and the bottom ruled ground line (`getGroundY()`).
- **Horizontal Speed Control:**
  - **Right (`→` / `D` / On-screen Right button):** Accelerates flight speed (`speed ++`), tilts/shifts the bird slightly forward, increases wing flap cadence, and spawns wind streak lines.
  - **Left (`←` / `A` / On-screen Left button):** Decelerates flight speed (`speed --`).
- **Coin Formations & Combo Progression:**
  - Coins feature hand-drawn outlines with `"1"` (and `"5"` golden bonus coins in higher levels) inside.
  - Patterns include: **Scattered** (matching the original hand sketch), **Sine Wave**, **Rainbow Arc**, **Diagonal Climb**, and **Zigzag**.
  - Consecutive catches build a streak multiplier up to **5x**; missing a coin resets the streak.

---

## 3. Feature Evolution & Current State
1. **Visual Aesthetic:**
   - Sketchbook paper background with toggleable paper styles: **Ruled Notebook** (with red margin line), **Graph Grid**, and **Clean Paper**.
   - Double-stroked graphite pencil outlines, feathered tail bristles with cross-ticks, asymmetric scalloped wings, round head, dot eye, and pointed beak.
2. **Timed Levels & Economy:**
   - Timed levels (~23 seconds) spawning 100 coins per level.
   - End-of-level summary awards 1–3 stars and deposits collected coins into a persistent bank (`localStorage`).
3. **Customization Store (3 Tabs):**
   - **Birds (Species):** Original Pencil Sketch, Flamingo, Goose, Parrot, Origami Crane, Phoenix, etc., with unique procedural drawings and flight perks.
   - **Dye Colors:** Recolor/dye unlocked birds.
   - **Accessories:** Hats, capes, and wearable doodles aligned to per-species anchor coordinates.
4. **Localization:**
   - Full **Hebrew (`dir="rtl"`)** localization across menus, HUD, store items, and level summaries.
5. **Audio:**
   - Procedural Web Audio synthesizer (`SketchAudio` class) for wing whooshes, pitch-scaling coin chimes, stage-up fanfares, and mute toggle.

---

## 4. File Structure in Repository
- `index.html` — Complete game source code (styles, UI overlays, canvas game loop, audio engine, and store data).
- `HANDOFF.md` — This context file for future development sessions.

---

## 5. How to Resume Development in Future Sessions
When starting a new chat to add features (e.g., obstacles/enemies, power-ups, background themes, boss levels, or soundtracks):
1. Upload or paste your latest `index.html` alongside this `HANDOFF.md` file.
2. Reference the existing systems inside `index.html`:
   - `SketchAudio` for sound effects.
   - `spawnCoinPattern()` for level/coin wave generation.
   - `drawSketchBird()` for procedural character, dye, and accessory rendering.
   - `localStorage` keys for persistent coins, unlocked birds, dyes, and accessories.

---

## 6. Roadmap / Ideas for Next Iterations
- [ ] Optional obstacles (paper airplanes, eraser blocks, ink blots, or storm clouds) in higher levels or a separate "Challenge Mode".
- [ ] Magnet, shield, and double-coin power-ups floating in the sky.
- [ ] New notebook themes (blackboard chalk mode, blueprint paper, sunset watercolor).
- [ ] Background music loop using Web Audio API.