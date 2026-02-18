# CLAUDE.md — Cosmere RPG Presentation

## Project Overview

Single-file SPA (`index.html`) for a Twitch livestream presentation of the Cosmere RPG. No build tools, no dependencies, no frameworks — everything is in one HTML file.

## File Structure

```
index.html   — The entire app (HTML + CSS + JS)
README.md    — User-facing documentation
CLAUDE.md    — This file
```

## Architecture

The app has three layers inside `index.html`:

1. **CSS** (`<style>`) — Custom properties at the top define the full color palette. All layout uses CSS Grid and Flexbox.
2. **HTML** (`<body>`) — Static shell: header, three `.tab-pane` divs (home/crunch/fluff), and the slide overlay. Card content is injected by JS.
3. **JavaScript** (`<script>`) — Vanilla JS. No frameworks. Key sections:
   - `CRUNCH` / `FLUFF` arrays — all card data and content
   - `switchTab()` — tab visibility logic
   - `buildCard()` / `renderGrids()` — card DOM generation
   - `openSlide()` / `closeSlide()` / `paintSlide()` / `moveSlide()` — overlay logic
   - `initStars()` — canvas animation loop
   - `toggleFullscreen()` — Fullscreen API wrapper

## Color Palette

All colors are CSS custom properties on `:root`. Do not hardcode colors — always reference a variable.

| Variable | Value | Use |
|---|---|---|
| `--royal` | `#1a3ea8` | Primary blue |
| `--gold` | `#c9a63d` | Primary accent |
| `--gold-light` | `#e5c05a` | Headings, highlighted text |
| `--white` | `#edf2ff` | Body text |
| `--white-dim` | `rgba(237,242,255,0.62)` | Secondary text |
| `--bg-deep` | `#030b1a` | Page background |
| `--bg-card` | `#102358` | Card backgrounds |

## Content Editing

All content the presenter will fill in lives in the `CRUNCH` and `FLUFF` arrays. Each entry is an object:

```js
{
  icon: '🎲',       // Emoji shown on card face
  tag: 'Foundation', // Small label above the title
  title: '...',      // Card title and slide heading
  excerpt: '...',    // Plain text shown on card face (no HTML)
  content: `...`     // HTML string rendered inside the slide overlay
}
```

Inside `content`, use only: `<p>`, `<h3>`, `<ul>`, `<li>`. Other tags will render but are unstyled.

## Conventions

- Keep everything in `index.html` — do not split into separate CSS/JS files unless the user explicitly requests it.
- Prefer editing existing CSS custom properties over adding new color values.
- Cards in CRUNCH and FLUFF should stay at 6 each unless the user asks to add/remove.
- Do not add external JS libraries or npm dependencies.
- When adding new interactive features, wire keyboard shortcuts and add them to the hints on the home screen.
- The star canvas must remain `position: fixed` at `z-index: 0`; all content sits at `z-index: 1` or above.

## User Preferences

- Colors: royal blue primary, gold + white accents — do not change the palette without being asked.
- Content is entered by the user; Claude should only add/edit structural placeholders, not write lore or rules text.
- This is for a Twitch livestream — prioritize readability at 1080p and large font sizes over information density.
