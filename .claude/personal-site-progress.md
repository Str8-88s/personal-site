# Claude Progress — Personal Site Project

## Current Status

**Phase:** Week 1 — In Progress
**Current Week:** Week 1
**Last Updated:** May 20, 2026
**Deployment Target:** Vercel
**Production URL:** TBD
**Domain:** `thomaswitherow.dev` (purchase when ready to go live)

---

## Plan

### Week 1
- [x] **Day 1–2:** Astro setup, Vercel skeleton deploy, CSS variable system + dark mode toggle
- [ ] **Day 3–4:** Homepage + Projects page
- [ ] **Day 5:** Blog infrastructure (content collection, index, post template)

### Week 2
- [ ] **Day 1:** Migrate `docs/blog-post.md` into Astro content collection as first post
- [ ] **Day 2:** Contact page + Formspree integration
- [ ] **Day 3–4:** Polish — typography, spacing, mobile (timebox aggressively)
- [ ] **Day 5:** Final review, blog post read-through, go live

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

---

## Environment

- OS: Windows (PowerShell)
- Editor: VS Code
- Node.js v24.15.0 ✓
- GitHub repo: `Str8-88s/personal-site`
- Deployment: Vercel
- Domain: `thomaswitherow.dev` (not yet purchased)

## File Structure (current)

```
personal-site/
├── .claude/
│   ├── personal-site-instructions.md
│   ├── personal-site-progress.md
│   └── personal-site-decisions.md
├── public/
│   └── styles/
│       └── global.css
├── src/
│   ├── layouts/
│   │   └── BaseLayout.astro
│   └── pages/
│       └── index.astro
├── .gitignore
├── astro.config.mjs
├── package.json
├── README.md
└── tsconfig.json
```

## Outstanding / Next Session

- Day 3–4: Homepage content (featured project card, latest blog preview) + Projects page
- Day 5: Blog infrastructure — Astro content collection, index page, post template
- Connect repo to Vercel for skeleton deploy (can do anytime)
