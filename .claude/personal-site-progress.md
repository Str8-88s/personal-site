# Claude Progress — Personal Site Project

## Current Status

**Phase:** Week 2 — Complete
**Current Week:** Week 2
**Last Updated:** June 8, 2026
**Deployment Target:** Vercel
**Production URL:** https://thomaswitherow.dev
**Domain:** `thomaswitherow.dev` ✓ (purchased June 8, 2026 via Porkbun — $9.81/yr)

---

## Plan

### Week 1
- [x] **Day 1–2:** Astro setup, Vercel skeleton deploy, CSS variable system + dark mode toggle
- [x] **Day 3–4:** Homepage + Projects page
- [x] **Day 5:** Blog infrastructure (content collection, index, post template)

### Week 2
- [x] **Day 1:** Migrate `docs/blog-post.md` into Astro content collection — reviewed and edited before migrating
- [x] **Day 2:** Polish pass — mobile, light mode, typography verified
- [x] **Day 3:** Domain purchased, DNS configured, site live at thomaswitherow.dev
- [ ] **Remaining:** Verify Formspree end to end on production URL
- [ ] **Remaining:** LinkedIn update — add live site URL and blog post link

---

## Session Log

### Session 1 — May 20, 2026
- Finalized stack: Astro + TypeScript + Vercel
- Finalized styling: slate/neutral palette, CSS custom properties, dark mode toggle
- Finalized site structure: `/`, `/projects`, `/blog`, `/blog/[slug]`, `/contact`
- Finalized 2-week build schedule

### Session 2 — May 20, 2026
- Astro scaffolded, foundation files created
- `public/styles/global.css`, `BaseLayout.astro`, `index.astro` with hero
- Dark mode toggle working, dev server at localhost:4321

### Session 3 — May 21, 2026
- Vercel connected — production URL live
- Fixed global.css 404 (was in `src/styles/`, moved to `public/styles/`)
- Added `--surface` CSS variable, button styles moved to global.css
- Homepage content: featured project card + blog preview
- Projects page built with detail blocks and tag list
- Blog infrastructure: `src/content.config.ts`, content collection, `[slug].astro`, `index.astro`
- Contact page: DuckDuckGo alias, GitHub/LinkedIn links, Formspree form (ID: `xnjrdolj`)
- Fixed GitHub email privacy push rejection

### Session 4 — May 23, 2026
- Blog post reviewed and edited before migrating
- Full blog post migrated to `src/content/blog/building-a-production-nodejs-api.md`
- Mobile responsiveness verified — all pages hold up at ~375px
- Light mode verified — both themes render correctly
- Site feature complete at Vercel URL

### Session 5 — June 8, 2026
- Purchased `thomaswitherow.dev` via Porkbun ($9.81/yr, includes free WHOIS privacy)
- Added domain in Vercel — deleted default Porkbun ALIAS + CNAME records, added A record pointing to `216.198.79.1`
- DNS propagating — site resolving at `thomaswitherow.dev`
- Old Vercel URL (`personal-site-gamma-lilac.vercel.app`) set to 307 redirect to `thomaswitherow.dev`

---

## Technical & Design Decisions Log

| Date | Decision | Choice | Why |
|------|----------|--------|-----|
| May 20 | Framework | Astro over Vite + React | Static-first, built-in content collections, island architecture |
| May 20 | Deployment | Vercel | Dead simple for static sites, free tier sufficient |
| May 20 | Styling | CSS custom properties | Dark mode via `[data-theme="dark"]` override, no flash on load |
| May 20 | Color palette | `#f8f8f8` light / `#1a1a2e` dark / `#3b5bdb` accent | Slate/neutral — professional, ages well |
| May 20 | Dark mode | Inline script in `<head>` reads localStorage before paint | Prevents flash |
| May 20 | Blog | Astro content collections | Built-in, type-safe, slug routing included |
| May 20 | Contact | Formspree | No backend needed, free tier sufficient |
| May 20 | Domain | `thomaswitherow.dev` | `.dev` is stronger signal for a developer |
| May 20 | Fonts | DM Sans + DM Mono via Google Fonts | Clean, professional, pairs well with slate palette |
| May 21 | CSS file location | `public/styles/global.css` | Astro serves static assets from `public/` — `src/styles/` 404s |
| May 21 | Button styles | In `global.css` not scoped styles | Scoped styles don't override global `a` tag rules reliably |
| May 21 | Content config | `src/content.config.ts` | Astro v5 moved config out of content folder |
| May 21 | Collection loader | Explicit `glob()` loader | Astro v5 requires explicit loader |
| May 21 | Post identifier | `post.id` not `post.slug` | Astro v5 glob loader uses `id` |
| May 21 | Contact email | DuckDuckGo alias | Forwards to real inbox without exposing it publicly |
| May 23 | Date frontmatter | ISO format `2026-05-18T00:00:00.000Z` | Astro v5 Zod schema requires parseable date — plain `YYYY-MM-DD` fails |
| Jun 8 | Domain registrar | Porkbun over Namecheap | Namecheap showed `thomaswitherow.dev` as "banned"; Porkbun had it available |
| Jun 8 | DNS config | A record `@` → `216.198.79.1` | Vercel's current recommended IP; deleted default Porkbun ALIAS + CNAME first |
| Jun 8 | Old URL handling | 307 redirect to `thomaswitherow.dev` | Keeps old Vercel URL working, forwards traffic to custom domain |

---

## Environment

- OS: Windows (PowerShell)
- Editor: VS Code
- Node.js v24.15.0 ✓
- GitHub repo: `Str8-88s/personal-site`
- Deployment: Vercel (auto-deploy on push to main)
- Production URL: https://thomaswitherow.dev
- Domain: `thomaswitherow.dev` — registered at Porkbun, $9.81/yr, renews ~$12.87/yr
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

1. **Formspree verify** — send a test submission from thomaswitherow.dev/contact
2. **LinkedIn update** — add thomaswitherow.dev and blog post link
3. **DNS confirm** — verify thomaswitherow.dev loads cleanly with HTTPS once propagation completes