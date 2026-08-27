# ICT Week Uzbekistan 2026 — Home Page (Vue 3 + Vite)

## Stack
- Vue 3 (`<script setup>`, Composition API)
- Vite
- Plain CSS with design tokens (no framework) — keeps the bundle small for Lighthouse Performance

## Run locally
```bash
npm install
npm run dev
```

## Build
```bash
npm run build
npm run preview
```

## Deploy
**Vercel**
```bash
npm i -g vercel
vercel --prod
```
**Netlify**
```bash
npm i -g netlify-cli
netlify deploy --prod --dir=dist
```
Framework preset: Vite. Build command: `npm run build`. Publish directory: `dist`.

## Structure
```
src/
  components/       one component per Figma block (header, hero, tabs, forms, etc.)
  views/Home.vue     assembles all sections in order
  assets/main.css    design tokens (colors, spacing, radius) + base/reset styles
```

## Responsive breakpoints
- Desktop: default (up to 1200px content width)
- Tablet: `max-width: 1024px`
- Mobile: `max-width: 640px`

## Important note on pixel-perfect accuracy
I built this from screenshots of the Figma desktop frame you shared, not from the live
Figma file itself (no Figma access here) — so:
- Real photos/logos need to be exported from Figma and dropped into `src/assets/images`,
  then swapped in for the placeholder gradient blocks (`hero__media`, `save__media`, tab
  card media, partner/attendee logos, etc.).
- Exact spacing/typography should be checked against Figma's Inspect panel once you have
  it open — I matched proportions and hierarchy from the screenshots as closely as
  possible, but true pixel-parity needs the actual file (font sizes, exact px gaps,
  color hex values from Figma's style panel).
- The Mobile/Tablet Figma frames weren't in the screenshots you sent, so those layouts
  here are my own responsive adaptation of the desktop design, not a direct match to
  Figma's dedicated Mobile/Tablet pages. If you can export those frames, I can adjust
  breakpoints to match exactly.

## Lighthouse checklist already covered
- Single small JS bundle, no unused UI framework
- `font-display: swap` via Google Fonts link, `preconnect` hints
- Semantic HTML (`header`, `main`, `nav`, `footer`, `section`), labeled form fields,
  `aria-*` attributes on toggles/dropdowns, focus-visible outlines
- Meta description/viewport/theme-color for SEO/best-practices
- No layout-shifting images (placeholders sized via CSS) — once you add real images,
  set explicit `width`/`height` or `aspect-ratio` to keep CLS low
