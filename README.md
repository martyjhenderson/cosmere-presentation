# Cosmere RPG — Livestream Presentation

A single-page presentation app for showcasing the **Cosmere RPG** on a Twitch livestream. Built with vanilla HTML, CSS, and JavaScript — no dependencies, no build step.

## Features

- **Crunch** section — game mechanics cards (dice system, character creation, combat, magic, etc.)
- **Fluff** section — lore & worldbuilding cards (the Cosmere, Roshar, factions, magic systems, etc.)
- Click any card to open a full slide overlay with prev/next navigation
- Animated star-field canvas background
- Fullscreen support for streaming
- Keyboard navigation

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `1` | Go to Home |
| `2` | Go to Crunch |
| `3` | Go to Fluff |
| `←` / `→` | Navigate between slides (when overlay is open) |
| `Esc` | Close slide overlay |
| `F` | Toggle fullscreen |

## Adding Your Content

All content lives in the `CRUNCH` and `FLUFF` arrays near the top of the `<script>` block in `index.html`. Each card looks like this:

```js
{
  icon: '🎲',
  tag: 'Foundation',
  title: 'Core Dice System',
  excerpt: 'Short description shown on the card.',
  content: `
    <p>Your HTML content goes here.</p>
    <h3>A Subheading</h3>
    <ul>
      <li>A bullet point</li>
    </ul>
  `
}
```

Replace the `[ placeholder ]` text in each card's `content` field with your own HTML. Supported tags inside `content`:

- `<p>` — paragraphs
- `<h3>` — subheadings (styled in gold)
- `<ul>` / `<li>` — bulleted lists (auto-styled with gold diamonds)

## Running Locally

Just open `index.html` in any modern browser — no server required.

```bash
open index.html
```

## Design

- **Primary color:** Royal blue (`#1a3ea8`)
- **Accents:** Gold (`#c9a63d`) and white (`#edf2ff`)
- **Fonts:** [Cinzel](https://fonts.google.com/specimen/Cinzel) (headings) + [Crimson Text](https://fonts.google.com/specimen/Crimson+Text) (body) via Google Fonts
