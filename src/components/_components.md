# Components

Organized by scope. Import from the closest folder that makes sense.

| Folder | What lives here |
|--------|----------------|
| `global/` | Nav, Footer, SEO head — used on every page |
| `blocks/` | Full-width page sections: Hero, TestimonialStrip, CtaBand, ClientLogoStrip, FeaturedWork |
| `cards/` | Repeating item UI: ServiceCard, ProjectCard, TeamCard, BlogCard |
| `ui/` | Atomic elements: Button, Accordion, Tag, Select, SectionHeader |

## Rules
- No page-level logic in components — keep them presentational
- All data passed via props; no direct data imports inside components
- Blog and portfolio cards share the same `ProjectCard` base where possible
