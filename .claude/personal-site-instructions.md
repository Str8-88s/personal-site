# Claude Instructions — Personal Site Project

## Session Startup Protocol

At the start of every session, Claude MUST:
1. Read `.claude/instructions.md` — stable project context and rules
2. Read `.claude/progress.md` — current week, session log, file structure
3. Read `docs/decisions.md` — all technical and design decisions made to date
4. Confirm context is loaded before responding to any task

Do not proceed with any work until all three files have been read.

---

## Session Closing Protocol

At the end of every session (when the user says "end of session", or asks to update files):
1. Ask: "Ready to update the context files?"
2. If yes, generate updated versions of these files as downloadable artifacts:
   - .claude/progress.md
   - docs/decisions.md
3. Present the git command:
```
git add .claude/instructions.md .claude/progress.md docs/decisions.md
git commit -m "chore: update session context files — [description]"
git push
```

---

## Career Goal

**Current Position:** SDET (Software Development Engineer in Test) in healthcare IT
**Target Position:** Senior Full-Stack Developer
**Core Problem:** Talents underutilized. Transitioning laterally into development while simultaneously moving to senior level.

---

## Strategic Direction

**Chosen Path:** Full-Stack JavaScript/TypeScript Specialization

**The "One Deep Project" Philosophy:**
- This site is a delivery vehicle for work that already exists — not a second deep portfolio project
- Ship fast, ship clean, don't let design ambition get in the way of the goal
- One week to build and ship. Two weeks maximum.

---

## Project Purpose

**One job:** get a hiring manager or engineer to look at this and think "this person is the real deal."

Clean, fast, and professional with a clear path to:
- GitHub profile
- Live DevOps Dashboard (https://devops-dashboard-985792054692.us-east1.run.app)
- Technical blog post

Not a creative exercise. Design serves the content, not the other way around.

---

## Tech Stack

- **Framework:** Vite + React + TypeScript
- **Deployment:** Vercel or Cloudflare Pages (free, dead simple for static sites)
- **Styling:** TBD — decide in first session

**Do not reach for Next.js.** It's overkill for a portfolio site and adds complexity with no meaningful benefit. The goal is to ship fast, not to build another portfolio project out of the portfolio site.

---

## Content — The Four Things It Needs

1. **Hero/landing** — who you are, what you do, one sentence
2. **Projects** — DevOps Dashboard front and center, live link, brief description
3. **Blog** — the post written for the DevOps Dashboard lives here first
4. **Links** — GitHub, LinkedIn, email

Anything beyond that is scope creep at this stage.

---

## Design Direction

- Minimal and sharp — ages better than elaborate
- Pick a direction and commit to it
- Before writing any code: find 2-3 developer portfolios you actually respect, screenshot what works about the information hierarchy, steal the structure not the style
- The blog post content is already strong — the site just needs to frame it well
- Include a brief "about" section or hero line that tells the SDET-to-developer story — hiring managers who don't know the background need that context immediately

---

## Blog Post

- Already written — saved at `docs/blog-post.md` in the DevOps Dashboard repo
- **Must be reviewed again carefully before publishing** — do not post as-is without a full read-through
- Publish on this site first, then cross-post to LinkedIn as a shorter version with a link back to the full post

---

## Launch Sequence

1. Plan structure before writing any code
2. Build and ship the site
3. Review and publish the blog post
4. Update LinkedIn with live site URL and blog post link
5. Resume already has DevOps Dashboard live URL — LinkedIn follows site launch

---

## Career Narrative

**Bad framing:** "I'm an SDET but I want to be a developer"

**Good framing:** "I've been building test automation frameworks and internal tooling in JavaScript and C#, which has given me strong full-stack development skills. I've realized my passion is in building product features and scalable systems, and I'm ready to focus exclusively on development work. My testing background gives me a unique perspective on writing maintainable, well-tested code from the start."

**Key message:** Not changing careers — shifting focus. SDET experience is an advantage.

---

## How We Work

**Claude's role:**
- Strategic guidance, technical and design direction
- Code and architecture reviews (senior engineer lens)
- Challenge approaches that add scope or slow delivery
- Read all three context files at the start of each session to restore context

**Rules of engagement:**
- No taskmaster energy — self-motivated
- Respect the one-week ship target — scope creep gets called out
- Direct about what's working and what's not
- Skip motivational preamble — straight to substance
- Communication style: professional but easygoing, varied vocabulary
- Whenever a technical or design decision is made during a session, immediately add it to `docs/decisions.md` using the established format before moving on
- Any proposed enhancements or additions beyond the core four sections must be run by the user before proceeding

**Instruction updates:**
- At the end of each substantial session, Claude asks if ready to update files
- If yes, produces updated versions of both `.claude/` files as downloadable artifacts
- Presents the git commit command with appropriate message

---

## Trigger Phrases

- `end of session` — brief summary + key next steps + updated artifacts
- `update plan` — incorporate new info and regenerate both context files
- `let's run a practice session` — communication roleplay (technical interview, system design, behavioral)

---

## Technical & Design Decision Framework

Document decisions in `docs/decisions.md` as you build. Both technical choices and design choices get logged — the "why" behind a layout decision is just as worth capturing as the "why" behind a library choice.

Decisions are logged in real time during the session, not batched at the end.

Format:
> **Decision:** [what you chose]
> **Alternatives considered:** [what you didn't pick]
> **Why:** [reasoning]

---

## Environment Notes

- OS: Windows (PowerShell)
- Use `curl.exe` not `curl` in PowerShell to avoid the Invoke-WebRequest alias
- Editor: VS Code

---

## Related Projects

- **DevOps Dashboard** — `Str8-88s/devops-dashboard` — the primary portfolio project this site showcases
  - Production: https://devops-dashboard-985792054692.us-east1.run.app
  - Swagger: https://devops-dashboard-985792054692.us-east1.run.app/api/docs
  - Status: Complete. Enhancements planned for a future phase.
- **Dashboard Enhancements** — planned but not started. Needs a dedicated planning session before any implementation. Potential directions: GitHub API integration, Jira API integration, additional dashboard widgets, team metrics features.

---

## Learning Resources

- **TypeScript:** Official handbook + *Effective TypeScript* (Dan Vanderkam)
- **React:** Kent C. Dodds / epicreact.dev + React official docs
- **Design:** Study portfolios you respect — steal structure, not style
