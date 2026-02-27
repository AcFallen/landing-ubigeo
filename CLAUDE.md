# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```sh
pnpm dev        # Start dev server at localhost:4321
pnpm build      # Build production site to ./dist/
pnpm preview    # Preview the production build locally
pnpm astro check  # Type-check .astro files
```

## Tech Stack

- **Astro 5** — static site generator with `.astro` component files
- **Tailwind CSS v4** — integrated via `@tailwindcss/vite` plugin (no `tailwind.config.*` file; configured through `astro.config.mjs`)
- **TypeScript** — strict mode (`tsconfig.json` extends `astro/tsconfigs/strict`)
- **pnpm** — package manager

## Architecture

Follows the standard Astro project layout:

- `src/pages/` — file-based routing; each `.astro` file becomes a route
- `src/layouts/` — base HTML shell components (`Layout.astro` wraps pages via `<slot />`)
- `src/components/` — reusable UI components
- `src/assets/` — images/SVGs imported directly into components (Astro handles optimization)
- `src/styles/global.css` — global styles; currently just `@import "tailwindcss"`
- `public/` — static files served as-is (favicons, etc.)

## Tailwind v4 Notes

Tailwind v4 does not use a config file — utility classes are available globally once `global.css` is imported in a page. Component-scoped styles in `.astro` files use `<style>` blocks (plain CSS, not Tailwind).
