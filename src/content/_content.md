# Content Collections

Astro content collections. Schemas enforced at build time via `config.ts`.

## portfolio/

One `.mdx` file per project. Frontmatter schema:

```ts
{
  title: string
  client: string
  year: number
  platforms: ('pc'|'console'|'mobile'|'vr'|'themepark')[]
  services: ('sound-design'|'music'|'technical-audio')[]
  cover: string           // path relative to public/
  heroMedia?: {
    type: 'video' | 'audio'
    src: string
    poster?: string
  }
  credits?: { role: string, name: string }[]
  featured?: boolean      // true = appears on homepage
  order?: number          // sort override
}
```

## blog/

One `.mdx` file per post. Frontmatter schema:

```ts
{
  title: string
  date: string            // ISO 8601: 2026-04-18
  category: 'post' | 'breakdown' | 'tutorial' | 'linkedin'
  excerpt: string         // 1–2 sentence summary for cards
  cover?: string          // optional, path relative to public/
  tags?: string[]
  published: boolean      // false = draft, won't render in prod
  originalUrl?: string    // for linkedin reposts, link to source
}
```

## Naming convention

- Portfolio: `client-project-name.mdx` (e.g. `firaxis-civ7.mdx`)
- Blog: `YYYY-MM-dd-post-title.mdx` (e.g. `2026-04-18-reverb-design.mdx`)
