# CLAUDE.md

Guidance for Claude Code (claude.ai/code) working in this repository.

## The site

"Keep Your Chi Up" — the marketing site for Jared Krupp's holistic health
practice. Two pages today: `index.html` (home) and `about.html` (about +
contact). `styles.css` is the only stylesheet.

Live at **https://www.jaredkrupp.com/**. The repo auto-deploys to Vercel on
every push to `main` — committing and pushing *is* deploying.

`vercel.json` sets `cleanUrls: true`, so pages are reached without the `.html`
extension (`/about`, `/thank-you`). Every new page and every internal link must
follow that convention.

## Brand voice

Compassionate and empathetic, but stern and direct — no beating around the
bush. Honor where people have been and what they've gone through, while
holding them to a high standard: they have the power within themselves to
change their lives, should they choose to.

The perspective comes from real experience — a registered nurse who trained as
a holistic practitioner, who has seen firsthand where the medical system fails
people, and who believes a truly holistic approach is the only route to
meaningful, lasting well-being.

Copy on the site is written in Jared's own first-person voice. Don't rewrite it
for tone or concision unless asked.

## Colors and fonts

Defined as CSS custom properties at the top of `styles.css`. Use the variables;
don't introduce new hex values.

| Variable | Value | Use |
|---|---|---|
| `--green` / `--ink` | `#374f2f` | Forest green — text, headings, footer |
| `--beige` | `#f5f5dc` | Page background |
| `--sage` | `#dde6d5` | Section backgrounds, cards |
| `--green-dark` | `#29391f` | Derived — button hover only |
| `--sage-deep` | `#cdd9c2` | Derived — borders, dividers |

Fonts (Google Fonts, loaded in each page's `<head>`):
- **Fraunces** — headings (`--font-head`)
- **Nunito Sans** — body (`--font-body`)

Nature motifs are inline SVG line work only — pine treelines, footer mountain
range. No photographs.

## Rules for every change

1. **Keep it simple and static.** Plain HTML and CSS. No frameworks, no build
   tools, no package manager, no dependencies.
2. **Always mobile responsive.** Check narrow widths before calling it done.
3. **Match the existing brand** — colors, fonts, voice, motifs — unless Jared
   says otherwise.
4. **Show the plan before writing code.** Get agreement first.
5. **Commit and push when done** so the change deploys.

## Structural gotcha

The header, footer, treeline-divider SVG, and nav-toggle script are duplicated
verbatim in both HTML files. There is no templating. Any change to one must be
mirrored in the other — including `aria-current="page"`, which moves to
whichever nav link matches the current page.

Accessibility is already wired in and should be preserved: skip link,
`:focus-visible` outlines, `aria-labelledby` on sections, `aria-hidden` on
decorative SVGs, and a `prefers-reduced-motion` block.

## Never

Do not store personal or private information in this file.
