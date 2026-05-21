# Decisions — Personal Site

Technical and design decisions made during development. Logged in real time during sessions.

Format:
> **Decision:** [what you chose]
> **Alternatives considered:** [what you didn't pick]
> **Why:** [reasoning]

---

**Decision:** Framework
**Choice:** Astro + TypeScript
**Alternatives considered:** Vite + React + TypeScript (original plan)
**Why:** Static-first by default, built-in content collections for the blog, island architecture means only the dark mode toggle ships JavaScript. Better fit than a full React SPA for a mostly-static portfolio site.

---

**Decision:** Deployment
**Choice:** Vercel
**Alternatives considered:** Cloudflare Pages
**Why:** Dead simple for static sites, free tier is sufficient, connects to GitHub repo in minutes.

---

**Decision:** Styling approach
**Choice:** CSS custom properties throughout
**Alternatives considered:** Tailwind, CSS modules
**Why:** Full control, no build dependency, pairs naturally with the dark mode toggle strategy. Custom properties on `:root` with `[data-theme="dark"]` override is clean and portable.

---

**Decision:** Color palette
**Choice:** `#f8f8f8` (light bg) / `#1a1a2e` (dark bg) / `#3b5bdb` (accent)
**Alternatives considered:** —
**Why:** Slate/neutral palette — professional, minimal, ages well. Avoids the generic "dark gray + green" developer portfolio look.

---

**Decision:** Dark mode implementation
**Choice:** Inline script in `<head>` reads `localStorage` before paint, toggle button writes back to `localStorage` and sets `data-theme` on `<html>`
**Alternatives considered:** CSS media query only (no toggle), JS after paint (causes flash)
**Why:** Reading localStorage before paint is the only way to prevent a flash of the wrong theme on page load. Must be placed before any stylesheets in `<head>`. Keeps toggle logic simple — no island component needed, just a plain script tag in the layout.

---

**Decision:** Blog infrastructure
**Choice:** Astro content collections
**Alternatives considered:** MDX files without content collections, external CMS
**Why:** Built-in to Astro, type-safe frontmatter, slug routing included. First post is `docs/blog-post.md` migrated from the DevOps Dashboard repo.

---

**Decision:** Contact form
**Choice:** Formspree
**Alternatives considered:** Custom backend endpoint, Netlify Forms
**Why:** No backend needed, free tier is 50 submissions/month (sufficient for a portfolio), integrates in minutes.

---

**Decision:** Domain
**Choice:** `thomaswitherow.dev`
**Alternatives considered:** `thomaswitherow.com`
**Why:** `.dev` is a stronger signal for a developer. Purchase when ready to go live.

---

**Decision:** Fonts
**Choice:** DM Sans (body) + DM Mono (code) via Google Fonts
**Alternatives considered:** System fonts, Inter
**Why:** DM Sans is clean and professional without being generic. DM Mono pairs naturally for code snippets. Both are variable-weight, load fast, and avoid the overused Inter look.

---

**Decision:** CSS file location
**Choice:** `public/styles/global.css` (served as static asset)
**Alternatives considered:** `src/styles/global.css` imported via bundler
**Why:** Linked via plain `<link>` tag in BaseLayout — Astro serves static assets from `public/`. Files in `src/styles/` return 404 when referenced by URL path.

---

**Decision:** Button styles location
**Choice:** `global.css` instead of scoped component `<style>` block
**Alternatives considered:** Scoped styles in index.astro
**Why:** Astro scoped styles don't reliably override the global `a { color: var(--accent) }` rule. Moving button styles to global.css ensures correct rendering across all pages.

---

**Decision:** Content config file location
**Choice:** `src/content.config.ts`
**Alternatives considered:** `src/content/config.ts` (Astro v4 style)
**Why:** Astro v5 moved the content config file out of the content folder. Old location throws LegacyContentConfigError.

---

**Decision:** Content collection loader
**Choice:** Explicit `glob()` loader in collection definition
**Alternatives considered:** No loader (v4 style)
**Why:** Astro v5 requires an explicit loader — the implicit loader was removed. `glob()` from `astro/loaders` is the standard replacement.

---

**Decision:** Post identifier
**Choice:** `post.id` instead of `post.slug`
**Alternatives considered:** `post.slug` (Astro v4 style)
**Why:** Astro v5 glob loader uses `id` as the identifier. `post.slug` no longer exists on collection entries.

---

**Decision:** Contact email
**Choice:** DuckDuckGo alias `shortness-pry-keg@duck.com`
**Alternatives considered:** Real Gmail address, GitHub noreply (outbound only)
**Why:** Forwards to real inbox without exposing it publicly. GitHub noreply only works for outbound commits, not inbound email.
