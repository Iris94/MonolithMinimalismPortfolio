# MonolithMinimalism

Astro portfolio site with pure CSS (no Tailwind), Nord color palette, and scoped component styles.

## Dev Commands

```sh
npm run dev     # localhost:4321
npm run build   # outputs to dist/
```

## Project Structure

```
src/
├── components/      # Reusable UI (fog.astro, navbar.astro)
├── sections/        # Page sections (landing-section.astro, about-section.astro)
├── pages/           # Astro pages (index.astro)
└── styles/          # CSS (root.css, base.css, global.css)
```

## CSS Architecture

- **`root.css`** — CSS variables only: colors (Nord palette), fonts, spacing
- **`base.css`** — Global resets, typography scale (h1-h6), layout (main-wrapper, content-area, right-sidenav, light-cube)
- **`global.css`** — Just imports base.css

All component-specific styles live in the component's `<style>` tag and are **scoped by Astro**.

## Components vs Sections

- **components/** — Reusable across pages (fog background, navbar with nav links + clock)
- **sections/** — Page-specific sections (landing-section with hero headings, about-section with profile image + bio)

## CSS Variables

Uses Nord palette: `--nord0` through `--nord15`, plus `--bg-color` (#f8f8f7) and `--font-heading` / `--font-body`.

## Key Layout Classes

- `.main-wrapper` — CSS Grid (5% 1fr auto), max-width 1920px, centered
- `.content-area` — Grid column 2, flex column, justify-content end
- `.right-sidenav` — Grid column 3, sticky, holds navbar component
- `.light-cube` — Fixed full-screen background (#f8f8f7)

## Typography Scale (base.css)

- h1: `clamp(12rem, 22vw, 20rem)` — largest, used for hero AI text
- h2: `clamp(6rem, 10vw, 9rem)` — second largest, used for hero DEVELOPMENT
- h3: `clamp(1.8rem, 3.5vw, 2.5rem)`
- h4: `1.75rem`
- h5: `1.25rem` with letter-spacing
- h6: `1rem` with letter-spacing

All headings: uppercase, Space Grotesk font, weight 700, line-height 1.1.

## Notes

- No Tailwind — pure CSS only
- Astro scoped `<style>` means classes don't leak globally across components
- Image assets go in `public/` and are served as-is
- `prefers-reduced-motion` handled in component keyframes