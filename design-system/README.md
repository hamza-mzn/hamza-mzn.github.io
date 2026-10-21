# Signal — design system

The design tokens behind this portfolio ([hamza-mzn.github.io](https://hamza-mzn.github.io/)),
extracted from `index.html` into a reusable layer. The feel is a **terminal at
night**: a deep blue-black canvas, hairline borders instead of shadows, one cool
cyan “signal” carrying every interaction, and a warm amber reserved for
attention.

## Files

- **`tokens.css`** — all design tokens as CSS custom properties on `:root`
  (colour, typography, spacing, radius, layout, the one elevation ring). Values
  are copied verbatim from the live `index.html`.

## Usage

1. Load the fonts in `<head>`:

   ```html
   <link rel="preconnect" href="https://fonts.googleapis.com">
   <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
   <link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500&family=IBM+Plex+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
   ```

2. Import the tokens before your own styles:

   ```html
   <link rel="stylesheet" href="design-system/tokens.css">
   ```

3. Reference variables instead of hard-coded values:

   ```css
   .button-primary {
     background: var(--signal);
     color: var(--ink);
     border-radius: var(--radius-sm);
     font-family: var(--sans);
   }
   .button-primary:hover { background: var(--signal-strong); }
   ```

## Principles

- **Dark by default.** A single dark theme. Most of the screen is `--ink`,
  `--surface` and `--text`; accents appear only where something is interactive
  or demands attention.
- **Borders, not shadows.** Separation comes from `--line`. The only shadow is
  `--ring-surface` (the portrait halo).
- **Cyan is the signal.** `--signal` means “you can act here” — links, primary
  buttons, the terminal prompt, category labels.
- **Amber is the alarm.** `--amber` is status and emphasis only: availability,
  the feature card’s left edge, headline figures, the focus ring.
- **Monospace means token.** Anything in `--mono` reads as a precise value: a
  command, a technology tag, a metric.

## Colour reference

| Role | Token | Hex |
|---|---|---|
| Page ground | `--ink` | `#0d1522` |
| Raised surface | `--surface` | `#131e30` |
| Hover / active | `--surface-2` | `#1a2840` |
| Code ground | `--terminal` | `#0a111c` |
| Borders | `--line` | `#26364f` |
| Primary text | `--text` | `#e4eaf3` |
| Secondary text | `--muted` | `#93a3ba` |
| Primary accent | `--signal` | `#5cc8ee` |
| Primary accent (hover) | `--signal-strong` | `#7dd5f3` |
| Attention accent | `--amber` | `#f0b44c` |

Every text colour clears WCAG AA on its intended ground: `--text` ≈ 15:1 on
`--ink`, `--muted` ≈ 7:1, `--signal` ≈ 9.7:1, `--amber` ≈ 10:1, and `--ink` on a
`--signal` fill ≈ 9.7:1. The focus ring is a 2px `--amber` outline at a 3px
offset.

## Accessibility note

`index.html` is unchanged by this extraction. To adopt the tokens there, replace
the inline `:root` block with an import of `tokens.css` and swap literal values
for `var(--…)` references.
