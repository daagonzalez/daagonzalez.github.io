# daagonzalez.com

Personal portfolio built with [Astro](https://astro.build). Static output, zero client-side JS.

## Develop

```bash
npm install
npm run dev      # http://localhost:4321
npm run check    # type-check .astro files
npm run build    # static site in dist/
npm run deploy   # build and push dist/ to the gh-pages branch
```

## Adding a project

Drop a Markdown file into `src/content/projects/`:

```md
---
title: Project name
summary: One-line description shown in lists.
stack: ["Angular", "Kafka"]
order: 4            # lower = shown first; top 3 appear on Home
link: https://...   # optional live demo
repo: https://...   # optional source
---

What it is, the problem it solved, your role, anything technically interesting.
```

Home, the Projects list, and the detail page pick it up automatically.

## Layout

- `src/styles/global.css` — design tokens (colors, type) and shared primitives
- `src/layouts/BaseLayout.astro` — page shell; takes a `current` prop for nav highlighting
- `src/components/Rail.astro` — left rail (name, role, nav)
- `public/resume.pdf` — the downloadable resume
