# LCDS design system

LCDS is a dark, cinematic system for an immersive content app: a near-black navy ground (`#001823`), a warm gold accent (`#cdac73`) and a steel-teal second voice (`#477f99`), set in Jost — a geometric sans standing in for the source Avenir. Content lives in full-bleed photographic key art; every card fades to black at the foot so a title reads over any image.

## How to use this

- Link the one stylesheet from every page — `<link rel="stylesheet" href="styles.css">` — and take every color, font, spacing, radius and shadow from its variables (`var(--color-*)`, `var(--font-*)`, `var(--space-*)`, `var(--radius-*)`, `var(--shadow-*)`). Never hard-code a hex, a font name or a px value the tokens already carry.
- Build with the classes below rather than inventing parallel ones; the component pages are plain HTML, so view source and copy the markup.
- `templates/` holds starting points a consuming project can copy whole.
- The whole system was derived from `theme.json`. To change the look, edit the tokens at the top of `styles.css` and keep `theme.json` and this guide in step.

## Direction

Full-bleed, cinematic, dark. Content is the hero: every rail is a horizontal-scrolling row of photographic cards, every hero is a full-width image with a left-aligned title over it. Buttons are true pills (`border-radius: 999px`); card corners stay a tight 8px so imagery reads like key art, not a soft app tile. Icon buttons and the nav rail are translucent frosted circles (`backdrop-filter: blur(20px)` + `rgba(255,255,255,.1)`) floating over imagery.

## Color

A near-black navy ground (`--color-bg`) with white text and two accents — `--color-accent` gold and `--color-accent-2` teal, each carrying a 100–900 tonal ramp in OKLCH so any step reads at consistent visual weight. Use light steps (100–300) for tinted text on dark fills, 500 as the role's base, 600–700 for hover/pressed. `--color-text-muted` / `--color-text-faint` (light greys) carry secondary and metadata text — never full white for anything but headlines and primary labels. Four flat category swatches (`--color-cat-cyan/green/rose/yellow`) tag content by topic — use only as small dots in `.tag`, never as fills.

## Type

Jost throughout — 800 weight for headings, 500 for buttons/labels, 400 for body — loaded as `--font-heading` / `--font-body` (the same family; weight carries the voice). No second typeface.

## Icons

Use Lucide icons (https://lucide.dev) at stroke-width 2 — thin and refined, sitting quietly inside the frosted circular buttons.

## Interaction states

Every interactive element gets a themed `:hover` and pressed state from the accent ramp — never browser defaults. Keyboard focus is `:focus-visible { outline: 2px solid var(--color-accent); outline-offset: 2px; }`. Disabled controls drop to 45% opacity.

## Components

| Class | What it is | Shown in |
| --- | --- | --- |
| `.btn` with `.btn-primary`, `.btn-secondary`, `.btn-ghost`, `.btn-icon`, `.btn-block`, `.btn-sm` | Actions — primary is a solid gold pill | components/buttons.html |
| `.filter-row` + `.filter-chip` (`.is-active`) | Horizontal filter/segmented choices | components/buttons.html |
| `.tag` with `.tag-dot`, `.tag-premium`, `.tag-neutral` | Small category/status labels | components/buttons.html |
| `.card-content`, `.card-quest`, `.card-atlas` (+ `.card-badge`, `.card-copy`, `.card-kicker`, `.card-title`) | Photographic content cards at three scales | components/cards.html |
| `.rail`, `.rail-head`, `.rail-title`, `.rail-add`, `.rail-track` | A horizontal-scrolling content row | components/cards.html |
| `.topbar`, `.topbar-brand`, `.topbar-actions`, `.sidebar`, `.sidebar-item` (`.is-active`) | The header bar and floating icon rail | components/navigation.html |
| `.player-frame`, `.player-play`, `.player-close` | A full-screen media player over key art | components/navigation.html |
| `.washed` | A photographic figure, desaturated and darkened slightly | foundations/image.html |
| `.field` + `label`, `.input`, `.radio` + `.dot`, `.check` + `.box`, `.seg` + `.seg-opt` | Form fields and choices on native elements | components/forms.html |
| `.dialog-backdrop` + `.dialog` (+ `.dialog-title`/`-body`/`-actions`) | A modal over its backdrop | components/dialog.html |

## Do

- Let imagery carry the page — cards, heroes and quest banners are photographs first, chrome second.
- Keep card corners tight (8px); reserve the pill radius for buttons, chips and icon circles.
- Float controls over imagery as frosted translucent circles, never solid opaque chrome.
- Use the teal accent-2 sparingly, as a kicker/label voice, so gold stays the one call-to-action color.

## Don't

- Do not lighten the ground into grey — it must read as near-black navy.
- Do not round card corners past 8–16px; that softness belongs to buttons and pills only, not photography.
- Do not use more than the four category swatches for tagging, and never as large fills.
- Do not introduce a second typeface; weight and size carry all the voice Jost needs.

## Files

- `styles.css` — the only stylesheet: tokens plus the component layer.
- `readme.md` — this guide.
- `theme.json` — the parameters these files were derived from.
- `thumbnail.html` — the project cover.
- `foundations/type.html`, `foundations/color.html`, `foundations/layout.html`, `foundations/icons.html`, `foundations/image.html`
- `components/buttons.html`, `components/cards.html`, `components/navigation.html`, `components/forms.html`, `components/dialog.html`
- `theme.html` — the theme's parameters rendered as a reference sheet.
- `templates/home/` — the ACCUEIL home dashboard.
- `templates/explorer/` — the EXPLORER content grid.
- `templates/player/` — the full-screen video/audio player.
- `assets/` — reference photography from the source app.
