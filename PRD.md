# Product Requirements Document
## Clean Cuts Interactive — Marketing Website
*Created: 2026-04-19 | Status: Approved — Ready to Build*

---

## 1. Overview

A static marketing website for Clean Cuts Interactive (CCI), a game audio studio. Public GitHub repo uses the alias **Soundwave Designs** to obscure client identity. The site serves two primary user journeys: prospective clients evaluating the studio, and prospective hires evaluating the team and culture.

---

## 2. Decided Stack

| Decision | Choice | Notes |
|----------|--------|-------|
| Framework | Astro | Static-first, content collections, component islands |
| Styling | Tailwind CSS v4 | Brand tokens via CSS custom properties |
| Content | Astro content collections + MDX | Portfolio and blog |
| Fonts | System stack | Single swap point in `src/styles/fonts.css` |
| Hosting | GitHub Pages | Repo: `soundwave-design`. Base path: `/soundwave-design/` |
| Media | Self-hosted in `public/media/` | Long-form via SoundCloud/YouTube lite-embeds |
| Contact form | Deferred | Mailto fallback until endpoint decided |

---

## 3. Brand

### Identity
- **Studio name:** Clean Cuts Interactive
- **Public alias:** Soundwave Designs
- **Tagline:** Audio Partners. Not Vendors.
- **Market:** Games / Interactive media

### Origin Story *(live in BRIEF.md — edit there)*
Soundwave Designs is spearheaded by a group of passionate sound designers who wanted to challenge the boundaries of game audio, without compromising aesthetic and vision. We love what we do. We love blazing new trails.

We live on the bleeding edge of new technology and find innovative solutions for an industry that continues to push the envelope of what is possible. World class sound design, expert implementation and innovative original music all come together to deliver depth and personality to the environment.

### Color Tokens *(approved 2026-04-18)*
| Token | Hex | Role |
|-------|-----|------|
| `--bg` | `#0C0B08` | Page background |
| `--surface` | `#181510` | Cards, panels |
| `--text` | `#F5EFE0` | Body copy — 17:1 on bg ✅ AAA |
| `--text-muted` | `#B4A282` | Secondary text — 7.9:1 on bg ✅ AAA |
| `--accent` | `#C9A55A` | Primary gold — 8.5:1 on bg ✅ AAA |
| `--accent-light` | `#E0C07A` | Hover states |
| `--accent-deep` | `#8A6E3A` | Tags, borders |

### Voice
- Refined, technical, confident — "research lab meets mix stage"
- Short sentences. No marketing bloat. Proof over claims.

### Assets Available
| Asset | Count | Location |
|-------|-------|----------|
| Logo SVG | 1 | `Print.svg` (repo root) |
| Logo PNG | 1 | `FullLogo_Transparent_NoBuffer.png` (repo root) |
| Team photos | 18 | `public/images/team/` |
| Portfolio covers | 10 | `public/images/portfolio/` |
| Client logos (SVG) | 11 | `public/images/clients/` — testing only |

---

## 4. Site Map

| Route | Page | Priority |
|-------|------|----------|
| `/` | Home | P1 |
| `/about/` | Studio story, team, awards | P1 |
| `/services/` | Sound Design, Music, Technical Audio | P1 |
| `/portfolio/` | Filterable project grid | P1 |
| `/portfolio/[slug]/` | Project case study | P1 |
| `/blog/` | Blog index (scaffold only) | P2 |
| `/blog/[slug]/` | Blog post | P2 |
| `/jobs/` | Roles, benefits, FAQ | P1 |
| `/contact/` | Form, address, socials | P1 |
| `/404` | Not found — with services strip + CTA band | P1 |

---

## 5. Page Requirements

### Home (`/`)
1. Hero — tagline, primary CTA → `/portfolio/`, secondary CTA → `/contact/`
2. Services strip — 2-column layout, CSS `:has()` hover wiring, no JS island *(approved 2026-04-19)*
   - Left column: large display text (`clamp(28px, 3.5vw, 52px)`, 700 weight, left-aligned). Default: *"For games, trailers, and interactive media."* — last word gold via `<em>`. Hover: fades to service descriptor at heading size (0.7s ease).
   - Right column: service name rows, `display: grid; grid-template-columns: 1fr 40px`, `→` arrow. No service numbers. Hovered row turns gold.
   - Static CTA below: "See all services →" → `/services/`
3. Featured work — 4–6 tiles from portfolio collection (`featured: true`)
4. Client logos — grayscale strip, 11 logos available
5. Testimonials — 2–4 rotating quotes
6. CTA band — "Work with us" → `/contact/`

### About (`/about/`)
Layout reference: hexanyaudio.com/about/. Content source: cleancutsinteractive.com/about/ with all CCI identifiers replaced ("Clean Cuts Interactive" → "Soundwave Designs", "CCI" → "we/us", studio origin obscured).

1. **Hero** — full-width dark, "About Us" heading. Stats strip below: `22 Creatives · 500+ Projects · 15+ Years` (placeholders — update in `about.json`).
2. **Origin story** — 2-column: large display text left, body copy right.
   - Heading: "Who We Are"
   - Copy: *"Born from a Grammy Award-winning recording studio in 2010, Soundwave Designs forged into the world of interactive audio, spearheaded by a group of passionate sound designers who wanted to challenge the boundaries of game audio, without compromising aesthetic and vision. We love what we do. We love blazing new trails. We live on the bleeding edge of new technology and find innovative solutions for an industry that continues to push the envelope of what is possible. World class sound design, expert implementation and innovative original music all come together to deliver depth and personality to the environment."*
   - CTA: "See Our Work →" → `/portfolio/`
3. **Team grid** — "CAST OF CHARACTERS" heading. Intro: *"Here is the group of amazing talented individuals that come together every day to make beautiful noise."* Portrait cards, data-driven from `team.json`. Each card: photo + name + quirky attribute list (3–5 bullets per member, sourced from live site). 18 photos available in `public/images/team/`.
   - *(Placeholder copy — update `team.json` with real attributes before launch)*
4. **Facility** — placeholder slots (no facility photos yet). Section heading: "Our Home". Two empty image blocks with `--surface` background and `[FACILITY PHOTO]` label.
5. **Awards strip** — data-driven from `awards.json`. Placeholder entries at scaffold. *(Update `awards.json` before launch)*

**Team data (from live site — identity retained, studio references removed):**
Tom Dao · Jonathan Miller · Reilly Jones · Hanna Choi · Cory Foley-Marsello · John Rigatuso · William Lowe · Roc Lee · David Murphy · Chuck Carr · Steve Dobias + remaining members from `public/images/team/` filenames.

### Services (`/services/`)
Section heading: **"Full Service Audio Co-Development"**
Subtitle (under heading): *"For games, trailers, and interactive media."* — styled in `--text-muted`

**Layout:** Two-column — left: vertical service list, right: sticky portfolio image stack (9 covers stacked, `position: sticky; top: 61px`, `overflow: hidden`). Parallax at 0.8× scroll speed (`will-change: transform`). No alternating bands. No icon grid. No per-service CTA. *(parallax speed approved 2026-04-19)*

**Each service item:** Number inline with title (`01 · Sound Design`) → body copy → capability chips. Gold left-border on hover/active.

**Chips:** `--text` color, `--accent-deep` border, subtle gold tint fill (`rgba(201,165,90,0.06)`).

**Page CTA:** Single "Start a project →" band at bottom of page only.

| # | Slug | Eyebrow | Title | Body | Capability Bullets |
|---|------|---------|-------|------|--------------------|
| 01 | `sound-design` | Games · Interactive | Sound Design | Designing sound is an art and a craft. Every hand-built asset is finely tuned to make an impact — weapons, abilities, ambiences, UI, foley, and everything in between. | Custom SFX, Haptics, Spatial / Immersive Audio, Dialogue Editing, Foley, UI Audio |
| 02 | `technical-audio` | Games · Interactive | Technical Audio | Sound is only half the equation. We embed directly into your pipeline — programming, implementation, and system design from pre-production through ship. | Wwise, FMOD, Unreal (Blueprints / C++), Unity (C#), Audio System Design, Proprietary Engine Integration |
| 03 | `trailer-cinematic` | Trailers · Cinematics | Trailer / Cinematic | A 30+ year legacy of award-winning sound design and audio mixing for high-profile linear projects. Every screen size. Every platform. *(original copy names studio — keep obscured)* | Trailer Sound Design, Cinematic Mixing, Audio Post, Broadcast Delivery |
| 04 | `original-music` | Games · Trailers | Original Music | Our composers are fluent in the language of games — orchestrating scores that drive the journey and stay with players long after the credits roll. | Original Composition, Orchestral Recording, Adaptive / Interactive Music Systems, Mixing & Mastering, Songwriting |
| 05 | `vo-pipeline` | Games · Interactive | VO Pipeline | Dialogue at scale, delivered clean. We build streamlined workflows for editing and mastering large volumes of VO — accurate, on schedule, every time. | VO Editing, Dialogue Mastering, Pipeline Design, Large-Volume Delivery |

Each band links to `/contact/?service=[slug]`

### Portfolio (`/portfolio/`)
- 16:9 cover grid, client-side filters (Service + Platform), sorted newest first
- 10 real entries available; scaffold supports 100+
- Service filters: `All | Sound Design | Technical Audio | Trailer/Cinematic | Original Music | VO Pipeline`
- Platform filters: `All | PC | Console | Mobile | VR | Theme Park`

### Portfolio Detail (`/portfolio/[slug]/`)
MDX-driven. Schema: title, client, year, platforms, services, cover, heroMedia?, credits?, featured?, order?
- `services` values: `'sound-design' | 'technical-audio' | 'trailer-cinematic' | 'original-music' | 'vo-pipeline'`

### Blog (`/blog/`) — scaffold only
Content categories: `post | breakdown | tutorial | linkedin`
- `linkedin` category includes `originalUrl` field for source link
- No content at launch — structure and routes only

### Jobs (`/jobs/`)
- Open roles from `jobs.json`
- Benefits grid from `benefits.json`
- FAQ accordion from `faq.json`

### Contact (`/contact/`)
- Address, phone, email (tap-to-action)
- Form: name, email, company (optional), project type (select: Sound Design / Technical Audio / Trailer/Cinematic / Original Music / VO Pipeline / Multiple / Other), message
- **Endpoint: deferred** — mailto fallback with TODO comment

### 404 (`/404`)
- **Main body (centered):** Large display heading: "404" (gold, `clamp(80px, 15vw, 160px)`). Subheading: "Page not found." Body: "Maybe you were looking for:" followed by nav links (Home, Services, Portfolio, About, Contact) as styled anchor list.
- **Below:** Services strip section (same component as home — 2-column hover layout).
- **Below:** CTA band (same component as home — "Ready to build something? Get in Touch").

---

## 6. Global Components

| Component | Description |
|-----------|-------------|
| `Nav` | Sticky, transparent over dark hero, solid otherwise. Mobile: hamburger overlay |
| `Footer` | Logo left, social icons center (LinkedIn, YouTube, Instagram), copyright right. No mega-footer. Socials appear in footer only — not on Contact page. *(approved 2026-04-19)* |
| `SEO` | Per-page title, description, OG, Twitter card, canonical |
| `Hero` | Full-width, tagline, dual CTAs |
| `ClientLogoStrip` | Grayscale logos, hover reveals color |
| `ServiceCard` | Icon, title, description, href |
| `ProjectCard` | 16:9 cover, title, tags |
| `TeamCard` | Photo, name, title |
| `Testimonial` | Quote, attribution |
| `SectionHeader` | Eyebrow, title, optional lede |
| `CTA` | Heading + button band |
| `Accordion` | For FAQ |

---

## 7. Data Files

| File | Powers |
|------|--------|
| `team.json` | About page team grid |
| `services.json` | Services page + home cards |
| `testimonials.json` | Home testimonial strip |
| `clients.json` | Home logo strip |
| `jobs.json` | Jobs page open roles |
| `benefits.json` | Jobs page benefits grid |
| `faq.json` | Jobs page accordion |
| `awards.json` | About page awards strip |
| `social.json` | Footer + contact socials |

All schemas validated with Zod at build time.

---

## 8. Accessibility & Performance

- Lighthouse ≥95: Performance, Accessibility, Best Practices, SEO — all pages
- WCAG AAA contrast for body text (verified — all tokens pass)
- Keyboard navigable end-to-end with visible focus states
- No autoplay audio or video
- Images: explicit width/height, AVIF/WebP with fallback, Astro `<Image>` component
- `prefers-reduced-motion` respected — disables scroll animations
- **Motion defaults:** Scroll-triggered fade-up (`opacity 0→1` + `translateY 20px→0`, 0.6s ease, 100ms stagger on grid items). No stat counter animations. No page transitions. No autoplay. All vars in `src/styles/motion.css`.
- **Disabling translateY:** Set `--motion-translate: 0px` in `motion.css` to reduce to opacity-only fade. Default: `--motion-translate: 20px`.

---

## 9. SEO

- Per-page `<title>` and `<meta name="description">`
- OpenGraph + Twitter card on every page
- Auto-generated `sitemap.xml` and `robots.txt`
- `schema.org/Organization` on home, `schema.org/CreativeWork` on project pages
- Canonical URLs throughout

---

## 10. Build Order

| Step | Scope |
|------|-------|
| 1 | Scaffold — Astro init, Tailwind, CSS tokens, base typography, Nav + Footer shell |
| 2 | Home — all sections with real/placeholder data |
| 3 | About + Services — static marketing pages |
| 4 | Portfolio grid + one project detail template |
| 5 | Blog scaffold — routes, schema, empty index (no content) |
| 6 | Jobs — data-driven roles, benefits, FAQ accordion |
| 7 | Contact — form shell, mailto fallback, socials |
| 8 | Polish — motion, image optimization, SEO meta, sitemap, OG images, 404 |
| 9 | Audit — Lighthouse, keyboard nav, reduced-motion, broken links |

---

## 11. Deferred / Out of Scope for v1

| Item | Status |
|------|--------|
| Contact form endpoint | Deferred — mailto fallback at launch |
| Client logo usage approval | Confirm with CCI before launch |
| Facility photography | No assets — placeholder blocks at launch |
| Blog content | Routes scaffolded, no posts at launch |
| Font pairing | System stack at launch, swap point in `fonts.css` |
| Audio/video samples | Placeholder slots only |
| Bilingual (EN/other) | Out of scope |
| CMS / admin UI | Out of scope |
| User accounts | Out of scope |

---

## 12. Easy Customizations — Where to Update Things

A reference for making common changes without hunting through the codebase.

| What to change | Where | Notes |
|----------------|-------|-------|
| **Font** | `src/styles/fonts.css` | Single swap point. Import the new font, update `--font-body` and `--font-display` custom properties. System stack is the default. |
| **Mobile breakpoints** | `src/styles/breakpoints.css` | Three vars: `--bp-sm: 640px`, `--bp-md: 768px`, `--bp-lg: 1024px`. Used as Tailwind screen overrides. Change here — updates all responsive rules globally. |
| **Motion speed / easing** | `src/styles/motion.css` | Vars: `--motion-duration: 0.6s`, `--motion-ease: cubic-bezier(0.16,1,0.3,1)`, `--motion-stagger: 100ms`, `--motion-translate: 20px`. Set `--motion-translate: 0px` for opacity-only fade. Set `--motion-duration: 0` to kill all motion. |
| **Social URLs** | `src/data/social.json` | Three entries: `linkedin`, `youtube`, `instagram`. Update `url` field for each. Footer reads from this file at build time. |
| **Color tokens** | `src/styles/tokens.css` | 7 tokens: `--bg`, `--surface`, `--text`, `--text-muted`, `--accent`, `--accent-light`, `--accent-deep`. Change here — updates everywhere. |
| **Hero copy** | `src/pages/index.astro` | Eyebrow, headline, and CTA button labels are inline in the Hero component call. |
| **Studio tagline** | `BRIEF.md` + `src/data/studio.json` | `BRIEF.md` is the source of truth for brand copy. `studio.json` feeds it into the build. |
| **Copyright year** | `src/components/Footer.astro` | One line. Or make it dynamic: `new Date().getFullYear()`. |
| **Contact email** | `src/data/studio.json` | `email` field — used in contact page and mailto fallback. |
| **Nav links** | `src/components/Nav.astro` | Order and labels are hardcoded in the component. Add/remove as needed. |
| **Services copy** | `src/data/services.json` | Title, body, chips per service. Slug drives the contact form `?service=` param. |
| **Parallax speed** | `src/components/ServicesImagePanel.astro` | One constant: `PARALLAX_SPEED = 0.8`. Tune in browser, update here. |
| **Client logos** | `src/data/clients.json` + `public/images/clients/` | Add/remove entries. `forceWhite: true` flag applies `filter: brightness(0) invert(1)`. |
| **Testimonials** | `src/data/testimonials.json` | Quote, attribution, optional title/company per entry. *(Placeholder copy at scaffold — replace before launch)* |
| **Team members** | `src/data/team.json` | Name, title, photo filename, attributes array (quirky bullets). *(Placeholder attributes at scaffold — verify before launch)* |
| **Awards** | `src/data/awards.json` | Name, year, category. *(Placeholder entries at scaffold — replace before launch)* |
| **Jobs / Benefits / FAQ** | `src/data/jobs.json`, `benefits.json`, `faq.json` | All scaffold with placeholder entries. Replace before launch. |
| **About page stats** | `src/data/about.json` | Three fields: `creatives`, `projects`, `years`. Default: `22`, `500+`, `15+`. |

---

## 13. Operator Inputs Still Needed

| Input | Status |
|-------|--------|
| `ADDRESS` | TODO — placeholder at build |
| `PHONE` | TODO — placeholder at build |
| `EMAIL` | TODO — placeholder at build |
| `SOCIAL` urls | TODO — placeholder at build |
| Testimonials content | TODO — scaffold with placeholder quotes |
| Awards data | TODO — scaffold with placeholder entries |
| Jobs / benefits / FAQ content | TODO — scaffold with placeholder entries |
