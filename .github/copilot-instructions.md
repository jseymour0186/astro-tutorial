# Copilot Instructions for Astro Tutorial Site

## Project Overview
This is a minimal **Astro 5.16** static site generator project. Astro renders `.astro` files to static HTML at build time, with optional JavaScript islands for interactivity. The project follows Astro's file-based routing convention.

## Architecture Essentials

### File Structure & Routing
- **`src/pages/`** — Each `.astro` or `.md` file automatically becomes a route (e.g., `index.astro` → `/`)
- **`public/`** — Static assets served as-is; referenced with `/` paths in templates
- **`src/components/`** (optional) — Reusable Astro/React/Vue/Svelte components, not exposed as routes

### Astro File Format
Each `.astro` file has a **component script** (top, between `---`) and **template** (bottom):
```astro
---
// Component logic, imports, props here
const title = "My Page";
---

<html>
  <h1>{title}</h1>
</html>
```
- Scripts run **server-side only** at build time — no client JS unless explicit
- Use `.astro` for layouts; use framework components (`.jsx`, `.vue`) for interactive islands

### Type Safety
- Extends `astro/tsconfigs/strict` in `tsconfig.json` — enforce strict type checking
- TypeScript required for all component scripts and integrations

## Development Workflow

**Core Commands** (all run from project root):
- `npm run dev` — Start local dev server at `http://localhost:4321` (hot reload enabled)
- `npm run build` — Compile to static HTML in `./dist/` directory
- `npm run preview` — Preview built site locally before deploy
- `npm run astro ...` — Run Astro CLI directly (e.g., `npm run astro add react`)

## Key Conventions

1. **Metadata & SEO** — Use `<head>` with `<meta name="generator" content={Astro.generator} />` to identify Astro-built pages
2. **Styling** — Scoped by default in `.astro` files; import CSS or use `<style>` tags for component-local styles
3. **Minimal Dependencies** — Only `astro` as runtime dependency; framework integrations added via CLI

## External Integrations
The project is intentionally minimal. Add integrations via `npm run astro add`:
- React, Vue, Svelte for interactive components
- Tailwind CSS for styling
- MDX for enhanced Markdown pages

## Common Tasks
- **Add a new page** → Create `.astro` in `src/pages/` (auto-routed by filename)
- **Add reusable component** → Create in `src/components/`, import in `.astro` pages
- **Static assets** → Place in `public/`, reference as `/filename` in templates
- **Configure builds** → Modify `astro.config.mjs` (currently empty defaults)
