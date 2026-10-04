---
title: Portfolio Site
summary: This site — a static, content-driven portfolio built with Astro and a single design token sheet.
stack: ["Astro", "TypeScript", "CSS"]
order: 1
link: https://daagonzalez.com
repo: https://github.com/daagonzalez/daagonzalez.github.io
---

## What it is

The site you're reading. A five-page portfolio with a persistent rail/content
layout, built to be quick to scan and easy to update.

## The problem

The previous version was a single-page Svelte app with Tailwind. It worked,
but adding a project meant editing component code, and it shipped a
JavaScript runtime for what is essentially static text.

## My role

Sole developer — design direction, implementation, and deployment.

## Technically interesting

- **Zero client-side JavaScript.** Every page is pre-rendered HTML and CSS.
- **Content collections.** Each project is a Markdown file with a typed
  frontmatter schema; the home page, project list, and detail pages all read
  from the collection, so adding a project is a one-file change.
- **One accent color.** All styling flows from a small set of CSS custom
  properties, with amber reserved for the current page, tags, and active
  states.
