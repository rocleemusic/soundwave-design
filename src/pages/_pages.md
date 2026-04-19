# Pages

One Astro file per route. Pages pull from `src/data/` and `src/content/` — no hardcoded copy in page files.

| File | Route | Primary data source |
|------|-------|-------------------|
| `index.astro` | `/` | `services.json`, `testimonials.json`, `clients.json`, portfolio collection (featured) |
| `about.astro` | `/about/` | `team.json`, `awards.json`, BRIEF.md origin story |
| `services.astro` | `/services/` | `services.json` |
| `portfolio/index.astro` | `/portfolio/` | portfolio collection |
| `portfolio/[...slug].astro` | `/portfolio/[slug]/` | portfolio collection entry |
| `blog/index.astro` | `/blog/` | blog collection |
| `blog/[...slug].astro` | `/blog/[slug]/` | blog collection entry |
| `jobs.astro` | `/jobs/` | `jobs.json`, `benefits.json`, `faq.json` |
| `contact.astro` | `/contact/` | `social.json`, form config |
| `404.astro` | `/404` | static |
