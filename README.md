# Debjeet Das | Interactive Portfolio

A single-file, zero-dependency portfolio for Debjeet Das, a Software Engineer at Amdocs (telecommunications) with 2 years of experience. Everything is procedural (CSS and vanilla JS): particle network background, glitch-neon hero, typing roles, scroll reveals, animated skill bars, and tilt-and-glow cards. Fully responsive, keyboard accessible, and honors `prefers-reduced-motion`.

## Interactive Mode (Enter / Exit Experience)

The hero button toggles the experience:

- **Enter Experience** scrolls to Level 1 (Games) and starts a subtle generative ambient pad (Web Audio API), a bottom-screen frequency visualizer, and a soft reactive glow.
- While the experience is running the button reads **Exit Experience**. Clicking it stops the audio and effects and scrolls back to the home page. A floating **Exit Experience** pill (bottom-right) also appears once you scroll down, so you can leave from any level.
- The small round button at the bottom-right mutes/unmutes the ambient audio. Clicking it before entering also starts the experience.

Respects `prefers-reduced-motion`.

## Navigation

Scroll normally, use the top navigation, press **← →** arrow keys, or **swipe left/right** to jump between sections ("levels"). A top progress bar and a right-edge level-dot rail track position, with a toast naming each level on entry.

The typing effect shows a blinking pink caret, and the text-selection caret is hidden so no white blinking cursor appears when you tap text.

## Sections

- **Hero**: glitch name, typing roles, interactive particle field, Enter/Exit Experience toggle, GitHub button
- **Games** (Level 1): 10 live browser games with genre filters; each card opens the game in a new tab
- **About** (Level 2): short narrative and animated counters
- **Experience** (Level 3): Software Engineer at Amdocs, 2 years
- **Skills** (Level 4): Java, Python, Flutter, C# with animated bars
- **Projects** (Level 5): hover-animated cards
- **Contact** (Final): tap email to compose (Gmail app on mobile, Gmail web on desktop) and copy-email / copy-phone buttons

## Experience philosophy

The site is framed as a journey, not a page: Boot (Hero) → Playground (Games) → Engineer Core (About) → Real-World Systems (Experience) → Capabilities (Skills) → Built Systems (Projects) → Exit Node (Contact). A one-time RGB "glitch" pattern-interrupt fires once per session near 35–45% scroll depth to create a memory spike (GPU-friendly, transform+filter only, respects `prefers-reduced-motion`).

## Personalization & engagement

- First visit: full intro. Return visits: a "WELCOME BACK" toast (via `localStorage.dd_visited`).
- Game cards write `dd_last` (last game opened) and `dd_count` (total games opened) to `localStorage`; a line above the game grid shows "Continue: game_name · You've opened N games."
- Opening a game briefly fades to black before the new tab opens, instead of an abrupt jump.
- A small share-icon button in the nav (top-right, beside Contact) copies the page URL, with brief inline feedback — deliberately understated so exploration stays the focus.

## Micro-interactions

Buttons, chips and cards spawn a small pointer-position ripple on press (`.rip`, transform+opacity only, ~550ms). A "Live System Insight" panel under About shows animated performance/uptime/accessibility bars as a lightweight nod to engineering rigor.

## Hero interaction: Slice / Impact

The hero canvas doubles as a reactive surface. Press-and-drag (or touch-and-drag) across the hero draws a short-lived neon slash trail that follows your motion, spawns an expanding energy ring where you first press, and makes the "Debjeet Das" name glow brighter the longer you drag. Release to hear a light impact tick if Interactive Mode is on.

**Controls**

- Desktop: click and drag (mouse down + move) anywhere over the hero.
- Mobile/tablet: press and drag a finger over the hero (touch is unified via Pointer Events, so it feels identical to the mouse version).
- Sound (whoosh on press, tick on release) only plays when **Enter Experience** / Interactive Mode is active, and only ever starts from a user gesture.

**Performance & fail-safes**

- Runs on the existing particle `<canvas>` — no extra DOM, no libraries, `requestAnimationFrame`-driven.
- Trail length auto-shortens on low-core-count or small-screen devices.
- Entirely skipped when `prefers-reduced-motion` is set — the rest of the hero still works normally.
- Never calls `preventDefault`, so page scroll and existing swipe navigation are unaffected.

## Resume, social preview & achievements

- **Resume**: the "Resume" button in the hero displays `resume.pdf` — a clean one-page resume.
- **Social preview**: `og-image.png` (1200×630, on-theme banner) is wired via Open Graph/Twitter meta tags so shared links show a real preview instead of nothing.
- **Achievements**: a small badge strip above the games grid unlocks quietly as you explore — first game opened, 3+ games opened, every level visited, Interactive Mode entered, and using Share. State persists via `localStorage.dd_ach`.

## Theme, shortcuts & cursor trail

- **Theme toggle**: the sun/moon icon in the nav (or the **T** key) switches between the dark neon theme and a light variant; choice persists via `localStorage.dd_theme`. **Dark is always the default** for first-time visitors regardless of OS preference. A full-viewport neon slash wipe covers the whole page (at any scroll position) before the palette swaps, then reveals the new theme — skipped when `prefers-reduced-motion` is set. The light theme uses its own deeper accent palette (teal/rose/violet instead of neon cyan/pink/purple) plus boosted glow/fill opacity, so every glow, particle, border, chip and button stays visible on white — it's not just the neon colors faded onto white.
- **Keyboard shortcuts**: on desktop, a brief hint pill ("← → navigate · G Games · A About · E Exp · S Skills · P Projects · C Contact") fades in a moment after load and dismisses on first key press or click. The letter keys jump straight to that section; arrow keys still step through levels.
- **Cursor trail**: on mouse-driven desktops only, a short neon-colored trail of dots follows the cursor (lerp-chained, `transform`-only). Automatically off on touch devices and under `prefers-reduced-motion`.

## Local preview

Open `index.html` in any browser, or run `python -m http.server`.

### Copyright (c) 2026 Your Name. All rights reserved
