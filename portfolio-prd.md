# PRD: Portfolio Rewrite — Muhammad Farras Jibran

## 1. Current State Audit

### Existing Content (farras-jibran.netlify.app)

**Hero:**
- "Hello, I'm Muhammad Farras Jibran."
- Software Engineer at IMP Studio, Jakarta Timur
- Bachelor's in Information Systems — Indonesia Open University (GPA 3.11)
- Passionate about Software Development & AI
- Tech stack badges: Next.js, React, React Native, Laravel, Django

**Projects (6):**
1. PINTAR (2022) — KEMENAG digital learning platform
2. Pusaka Super Apps (2023) — Cross-platform mobile app for KEMENAG (React Native + Django + Laravel + Next.js)
3. Waste Management System (2025) — KEMENKES waste tracking (Next.js, Node.js, React Native)
4. Digital Signature KEMENAG — Laravel-based e-signature system
5. PBSB KEMENAG — Scholarship management for santri
6. BIB KEMENAG — Beasiswa Indonesia Bangkit (KEMENAG + LPDP)

**Experience:**
- Informatika Media Pratama — Software Engineer (Frontend), Oct 2021 – Present
- Informatika Media Pratama — Lead Engineer, Nov 2022 – Nov 2023
- Rumah Coding Indonesia — Freelance Trainer, Feb 2021 – Jun 2022

**Education:**
- Indonesia Open University — Bachelor's, Information Systems (Sep 2022 – Present), GPA 3.11

**Skills:**
- Programming: TypeScript, JavaScript, Python, PHP, SQL, React Native
- Web: React, Next.js, Django, Redux, Laravel
- Databases: MongoDB, Redis, MySQL, Firebase

**Contact:** farasjibran@gmail.com

### Current Design Issues
- Template by hrishikeshpaul (not custom) — generic look
- White background, Urbanist font, no visual identity
- No dark mode
- Project cards lack screenshots/visuals
- Skills section is just text lists — no visual treatment
- No animations or micro-interactions
- No case study depth on projects
- Footer credits another developer

---

## 2. Goals

| # | Goal | Success Metric |
|---|------|----------------|
| 1 | Look like a senior engineer's portfolio, not a template | Custom design, no third-party credit in footer |
| 2 | Modern 2025/2026 design language | Dark mode default, smooth animations, glassmorphism or bento grid |
| 3 | Highlight government-scale project work | Each project gets a case study card with metrics |
| 4 | Fast (Lighthouse 95+) | Static site, optimized images, no heavy JS frameworks |
| 5 | Mobile-first responsive | Works perfectly on phone, tablet, desktop |
| 6 | Easy to update | Content in JSON/markdown, not hardcoded in components |

---

## 3. Design Direction

### Aesthetic: "Dark Tech Minimal"
- **Dark mode default** with light mode toggle
- Monochrome base (near-black bg, white text) with ONE accent color (suggest: electric blue `#3B82F6` or emerald `#10B981`)
- Bento grid layout for projects (asymmetric, mixed sizes)
- Subtle grain/noise texture on background
- Glassmorphism cards with backdrop-blur
- Smooth scroll-triggered animations (fade-in, slide-up)
- Typography: Inter or Geist (clean, modern, free)

### Layout (top to bottom):
1. **Hero** — Full viewport. Name + title + animated gradient text. Social links. Scroll indicator.
2. **About** — Short bio with a subtle avatar/photo. Tech stack as animated icon row.
3. **Experience** — Timeline layout with company logos. Expandable detail cards.
4. **Projects** — Bento grid. Each card: thumbnail, title, tags, short description. Click → full case study modal/page.
5. **Skills** — Categorized with visual treatment (icon grid or progress bars, not plain text).
6. **Education** — Minimal, one card.
7. **Contact** — Email CTA + social links. Simple form (optional).
8. **Footer** — "Built by Muhammad Farras Jibran" + year.

### Animations:
- Page load: staggered fade-in of hero elements
- Scroll: sections fade-in/slide-up on viewport entry (Intersection Observer)
- Hover: cards lift with shadow + slight scale
- Cursor: custom cursor dot/outline (optional, low priority)
- Smooth anchor scrolling

---

## 4. Tech Stack (Recommended)

| Layer | Choice | Why |
|-------|--------|-----|
| Framework | **Astro** (static site) | Fastest possible output, zero JS by default, islands architecture for interactive bits |
| Styling | **Tailwind CSS** | Utility-first, dark mode built-in, easy responsive |
| Animations | **Framer Motion** or **GSAP** (via Astro island) | Smooth scroll-triggered animations |
| Content | Markdown/JSON files | Easy to update without touching components |
| Hosting | **Netlify** (keep current) | Already deployed there |
| Icons | **Lucide** or **Iconify** | Clean, consistent icon set |
| Fonts | **Geist** (Vercel's font) or **Inter** | Modern, readable, free |

### Alternatives:
- **Next.js** if you want SSR/SSG + React ecosystem (heavier but you already know it)
- **SvelteKit** if you want max performance with less JS

---

## 5. Content Rewrite Strategy

### Hero
- Remove "👋" emoji. Keep it clean.
- Title: "Software Engineer" (not "aspiring")
- Subtitle: "Building scalable systems for Indonesia's government sector"
- Add GitHub, LinkedIn, Email links as icon buttons

### Projects — Rewrite Each as Case Study
For each project, extract:
- **Problem** — What challenge did KEMENAG/KEMENKES face?
- **Solution** — What you built, architecture decisions
- **Impact** — Scale (users served, documents processed, etc.)
- **Tech** — Stack used, displayed as tags

Example rewrite for PINTAR:
> **PINTAR** — Digital Learning Platform for KEMENAG
> Built a web-based training platform serving thousands of ministry employees. Architected with [stack] to handle concurrent users and content delivery.
> Tags: `Next.js` `Laravel` `MySQL`

### Experience — Quantify
- Add metrics where possible (team size, performance improvements %)
- Remove generic bullet points ("Stayed current with emerging technologies")
- Keep only the strongest 3-4 bullets per role

### Skills — Visual
- Group as icon grid: each skill gets its logo/icon
- No progress bars (they're arbitrary and meaningless)
- Categories: Frontend / Backend / Mobile / Database / Tools

---

## 6. File Structure

```
portfolio/
├── src/
│   ├── content/
│   │   ├── projects.json        # All project data
│   │   ├── experience.json      # Work history
│   │   └── skills.json          # Skills by category
│   ├── components/
│   │   ├── Hero.astro
│   │   ├── About.astro
│   │   ├── Experience.astro
│   │   ├── Projects.astro
│   │   ├── ProjectCard.astro
│   │   ├── Skills.astro
│   │   ├── Contact.astro
│   │   └── ThemeToggle.astro
│   ├── layouts/
│   │   └── Layout.astro
│   └── pages/
│       └── index.astro
├── public/
│   ├── projects/                # Project screenshots
│   └── favicon.svg
├── astro.config.mjs
├── tailwind.config.mjs
└── package.json
```

---

## 7. Implementation Phases

### Phase 1 — Scaffold (30 min)
- `npm create astro@latest`
- Install Tailwind, configure dark mode
- Setup base layout + fonts

### Phase 2 — Content (1 hr)
- Write projects.json, experience.json, skills.json
- Rewrite all copy (remove fluff, add metrics)

### Phase 3 — Components (2-3 hrs)
- Build each section component
- Implement bento grid for projects
- Timeline for experience
- Icon grid for skills

### Phase 4 — Polish (1-2 hrs)
- Add scroll animations (Intersection Observer or Framer Motion)
- Dark/light toggle
- Responsive testing
- Lighthouse audit + fixes

### Phase 5 — Deploy (15 min)
- Push to GitHub
- Connect Netlify (or keep existing)
- Custom domain setup (if desired)

---

## 8. Content to Prepare

Before coding, gather:
- [ ] Project screenshots (6 projects)
- [ ] Professional photo/avatar (optional)
- [ ] GitHub profile URL
- [ ] LinkedIn profile URL
- [ ] Any metrics for projects (users, uptime, etc.)
- [ ] Preferred accent color

---

## 9. Out of Scope

- Blog section (can add later)
- CMS integration (content stays in JSON/markdown)
- Multi-language (Indonesian + English can be Phase 2)
- Analytics (can add Plausible/Umami later)

---

## 10. Risks

| Risk | Mitigation |
|------|------------|
| No project screenshots available | Use gradient placeholder cards with project initials |
| Astro learning curve | You already know React — Astro islands feel familiar |
| Animation performance | Use CSS-only where possible, JS only for scroll triggers |
| Content feels thin | Focus on quality over quantity — 4 strong case studies > 6 weak cards |

---

*PRD ready. Next step: confirm design direction + tech stack, then start building.*
