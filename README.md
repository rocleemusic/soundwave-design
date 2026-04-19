# Clean Cuts Interactive — Website

Astro + Tailwind CSS. Static build. Deploys to GitHub Pages.

---

## Quick Start

```bash
npm install
npm run dev        # localhost:4321
npm run build      # output: dist/
npm run preview    # preview build locally
```

---

## Where Things Live

| What | Where |
|------|-------|
| Studio identity, brand voice, design direction | `BRIEF.md` |
| Brand color tokens | `src/styles/global.css` → `:root` |
| Font swap point | `src/styles/fonts.css` |
| Page files | `src/pages/` — one `.astro` file per route |
| Reusable components | `src/components/` — see `_components.md` |
| Portfolio entries (MDX) | `src/content/portfolio/` |
| Blog entries (MDX) | `src/content/blog/` |
| JSON content (team, services, clients, etc.) | `src/data/` — see `_data.md` |
| Static assets (audio, images, favicon) | `public/` — see `_public.md` |
| Work-in-progress drafts | `drafts/` |
| Content collection schemas | `src/content/config.ts` |

---

## How to Edit Content

### Add a portfolio project
1. Create `src/content/portfolio/project-name.mdx`
2. Fill in frontmatter (see schema in `src/content/_content.md`)
3. Add cover image to `public/images/portfolio/`
4. Set `featured: true` to surface on homepage

### Add a blog post
1. Create `src/content/blog/post-title.mdx`
2. Set `category` to one of: `post` | `breakdown` | `tutorial` | `linkedin`
3. Add cover image to `public/images/blog/` if applicable

### Update team, services, clients, jobs
Edit the relevant JSON file in `src/data/`. Schema for each is documented in `src/data/_data.md`.

### Swap brand colors
Edit the 5 CSS custom properties in `src/styles/global.css` → `:root`. Tailwind reads from these.

---

## Site Map

| Route | File | Notes |
|-------|------|-------|
| `/` | `src/pages/index.astro` | Hero, services summary, featured work, testimonials |
| `/about/` | `src/pages/about.astro` | Origin story, facility, team, awards |
| `/services/` | `src/pages/services.astro` | Sound Design, Music, Technical Audio pillars |
| `/portfolio/` | `src/pages/portfolio/index.astro` | Filterable project grid |
| `/portfolio/[slug]/` | `src/pages/portfolio/[...slug].astro` | Project case study |
| `/blog/` | `src/pages/blog/index.astro` | Blog index (scaffold only at launch) |
| `/blog/[slug]/` | `src/pages/blog/[...slug].astro` | Individual post |
| `/jobs/` | `src/pages/jobs.astro` | Roles, benefits, FAQ |
| `/contact/` | `src/pages/contact.astro` | Form, address, socials |
| `/404` | `src/pages/404.astro` | Not found |

---

## Deploy (GitHub Pages)

```bash
npm run build
# Push dist/ or configure GitHub Actions to build on push to main
```

GitHub Pages config lives in `astro.config.mjs` → `site` and `base`. Repo name: `soundwave-design`. Deploy URL will be `https://[username].github.io/soundwave-design/` — set `base: '/soundwave-design/'` in Astro config.
