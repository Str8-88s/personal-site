# Claude Progress — Personal Site Project

## Current Status

**Phase:** Week 1 — Complete
**Current Week:** Week 2
**Last Updated:** May 21, 2026
**Deployment Target:** Vercel
**Production URL:** https://personal-site-gamma-lilac.vercel.app/
**Domain:** `thomaswitherow.dev` (purchase when ready to go live)

---

## Plan

### Week 1
- [x] **Day 1–2:** Astro setup, Vercel skeleton deploy, CSS variable system + dark mode toggle
- [x] **Day 3–4:** Homepage + Projects page
- [x] **Day 5:** Blog infrastructure (content collection, index, post template)

### Week 2
- [ ] **Day 1:** Migrate `docs/blog-post.md` into Astro content collection as first post — full review pass before publishing
- [ ] **Day 2:** Contact page polish + Formspree verification
- [ ] **Day 3–4:** Polish — typography, spacing, mobile (timebox aggressively)
- [ ] **Day 5:** Final review, go live

---

## Session Log

### Session 1 — May 20, 2026
- Finalized stack: Astro + TypeScript + Vercel
- Finalized styling: slate/neutral palette, CSS custom properties, dark mode toggle
- Finalized site structure: `/`, `/projects`, `/blog`, `/blog/[slug]`, `/contact`
- Finalized 2-week build schedule
- Context files updated

### Session 2 — May 20, 2026
- Astro scaffolded via `npm create astro@latest` — empty template, strict TypeScript
- Resolved nested folder issue (scaffold created `personal-site/personal-site/`) — moved files up via PowerShell
- Foundation files created:
  - `public/styles/global.css` — full CSS variable system (light/dark), reset, typography, layout utilities
  - `src/layouts/BaseLayout.astro` — base HTML shell with inline dark mode script (prevents flash), Google Fonts (DM Sans + DM Mono), sticky header with nav, footer
  - `src/pages/index.astro` — hero section wired to BaseLayout, CTA buttons
- Dark mode toggle implemented: inline script in `<head>` reads localStorage before paint, button toggles `data-theme` on `<html>` and writes to localStorage
- Dev server confirmed running at localhost:4321

### Session 3 — May 21, 2026
- Vercel connected to `Str8-88s/personal-site` — auto-detected Astro, deployed in minutes
- Production URL: https://personal-site-gamma-lilac.vercel.app/
- Fixed global.css 404 — file was in `src/styles/` instead of `public/styles/`; moved to correct location
- Added `--surface` CSS variable to both light and dark theme
- Added button styles to `global.css` (moved out of scoped component styles to fix rendering)
- Homepage content added: featured project card (DevOps Dashboard) + blog preview section
- Projects page built: detailed project card with "What it does" and "Infrastructure" detail blocks, full tag list
- Blog infrastructure built:
  - `src/content.config.ts` — Astro v5 content collection config with glob loader
  - `src/content/blog/building-a-production-nodejs-api.md` — placeholder post
  - `src/pages/blog/index.astro` — blog index with sorted posts
  - `src/pages/blog/[slug].astro` — dynamic post template
- Contact page built: DuckDuckGo alias email, GitHub/LinkedIn links, Formspree form
- Fixed GitHub email privacy push rejection — set noreply email in git config
- **Commits:**
  - `feat: homepage content — featured project card and blog preview`
  - `feat: projects page`
  - `feat: blog infrastructure — content collection, index, post template`
  - `feat: contact page with Formspree form`

---

## Technical & Design Decisions Log

| Date | Decision | Choice | Why |
|------|----------|--------|-----|
| May 20 | Framework | Astro over Vite + React | Static-first, built-in content collections, island architecture — only dark mode toggle ships JS |
| May 20 | Deployment | Vercel | Dead simple for static sites, free tier sufficient |
| May 20 | Styling | CSS custom properties throughout | Dark mode via `[data-theme="dark"]` override, no flash on load via inline script in `<head>` |
| May 20 | Color palette | `#f8f8f8` light / `#1a1a2e` dark / `#3b5bdb` accent | Slate/neutral — professional, ages well |
| May 20 | Dark mode implementation | Inline script in `<head>` reads localStorage before paint | Prevents flash; must run before stylesheets |
| May 20 | Blog | Astro content collections | Built-in, type-safe, slug routing included |
| May 20 | Contact | Formspree | No backend needed; free tier is 50 submissions/month — sufficient for portfolio |
| May 20 | Domain | `thomaswitherow.dev` | `.dev` is stronger signal for a developer than `.com` |
| May 20 | Fonts | DM Sans + DM Mono via Google Fonts | Clean, professional, distinctive without being loud — pairs well with the slate palette |
| May 21 | CSS file location | `public/styles/global.css` | Astro serves static assets from `public/` — files in `src/styles/` 404 when referenced via `<link>` tag |
| May 21 | Button styles | In `global.css` not scoped component styles | Scoped Astro styles don't reliably override global `a` tag rules; global wins |
| May 21 | Content config location | `src/content.config.ts` (not `src/content/config.ts`) | Astro v5 moved config file out of content folder |
| May 21 | Content collection loader | `glob()` loader explicitly defined | Astro v5 requires explicit loader — v4 style without loader throws LegacyContentConfigError |
| May 21 | Post slug | `post.id` not `post.slug` | Astro v5 glob loader uses `id` instead of `slug` |
| May 21 | Contact email | DuckDuckGo alias `shortness-pry-keg@duck.com` | Forwards to real inbox without exposing it publicly |

---

## Environment

- OS: Windows (PowerShell)
- Editor: VS Code
- Node.js v24.15.0 ✓
- GitHub repo: `Str8-88s/personal-site`
- Deployment: Vercel (auto-deploy on push to main)
- Production URL: https://personal-site-gamma-lilac.vercel.app/
- Domain: `thomaswitherow.dev` (not yet purchased)
- Formspree form ID: `xnjrdolj`

## File Structure (current)

```
personal-site/
├── .claude/
│   ├── personal-site-instructions.md
│   ├── personal-site-progress.md
│   └── personal-site-decisions.md
├── public/
│   ├── styles/
│   │   └── global.css
│   ├── favicon.ico
│   └── favicon.svg
├── src/
│   ├── content/
│   │   └── blog/
│   │       └── building-a-production-nodejs-api.md
│   ├── layouts/
│   │   └── BaseLayout.astro
│   └── pages/
│       ├── blog/
│       │   ├── [slug].astro
│       │   └── index.astro
│       ├── contact.astro
│       ├── index.astro
│       └── projects.astro
├── .gitignore
├── astro.config.mjs
├── content.config.ts
├── package.json
├── README.md
└── tsconfig.json
```

## Outstanding / Next Session

1. **Blog post migration** — copy full content from `docs/blog-post.md` into `src/content/blog/building-a-production-nodejs-api.md` after careful review pass
2. **Polish pass** — typography, spacing, mobile responsiveness (timebox to 1 day)
3. **Verify Formspree** — send a test submission to confirm emails arrive at DuckDuckGo alias
4. **Go live** — final review, purchase `thomaswitherow.dev`, point to Vercel
