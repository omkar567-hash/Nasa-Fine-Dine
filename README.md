# NIGHTFALL RACING — Phase 1 (Menu + Street Racing panel)

*Own the Streets. Rule the Night.*

Playable browser prototype of the main menu and the Street Racing selection panel.
No racing gameplay yet — the mode cards show a "Coming Soon" message by design.

## How to run

**Easiest:** double-click `index.html` (works in Chrome, Edge, Firefox). No install, no server, no internet needed.

**Optional local server:**
```
cd nightfall-racing
python -m http.server 8000     # then open http://localhost:8000
```

## Structure

```
nightfall-racing/
├── index.html          Markup: main menu, Street Racing panel, settings, exit dialog, shared SVG car art
├── css/styles.css      All styling, animations, responsive rules, low-graphics mode
├── js/background.js    Canvas night-city background + automatic low-graphics fallback
└── js/main.js          Navigation, "Coming Soon" toasts, settings, keyboard support
```

## Navigation

- Main Menu → **STREET RACING** → full-screen Street Racing panel
- **BACK** (or `Esc`) → Main Menu
- Mode cards (click / Enter / Space) → "Coming Soon" toast
- PLAY / GARAGE → "Coming Soon" toast; SETTINGS → dialog; EXIT → closes tab if allowed, otherwise a goodbye dialog

## Performance

- No libraries, no image files: everything is HTML/CSS/SVG + one Canvas 2D background (~35 KB total).
- Three.js was deliberately **not** used — it isn't needed for a menu and would add ~600 KB plus GPU load.
- Background is capped at 30 fps, pixel ratio 1, pauses when the tab is hidden.
- **Auto** graphics mode measures FPS and switches to a static single-frame background if the machine is slow.
  Force it in Settings → Graphics quality → Low. "Reduce motion" turns off card animations.

## Next phases

Each racing mode (Underground + Highway, Drift Challenge, Drag Racing) can plug in where the card click handler lives in `js/main.js`.
