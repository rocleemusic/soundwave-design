# Data Files

JSON files for all editable structured content. Edit these directly — no code changes needed.

| File | What it controls | Key fields |
|------|-----------------|------------|
| `team.json` | About page team grid | `name, title, role, photo, bio?, order?` |
| `services.json` | Services page pillars + homepage cards | `slug, title, description, bullets[], sampleMedia?` |
| `testimonials.json` | Homepage testimonial strip | `quote, name, role, company, project?` |
| `clients.json` | Homepage logo strip | `name, logo` |
| `jobs.json` | Jobs page open roles | `title, team, location, description, applyUrl` |
| `benefits.json` | Jobs page benefits grid | `icon, title, description` |
| `faq.json` | Jobs page FAQ accordion | `question, answer` |
| `awards.json` | About page awards strip | `year, org, category, project, result: 'won'|'nominated'` |
| `social.json` | Footer + contact social links | `platform, url` |

## To add a team member
Add an object to `team.json`. Add photo to `public/images/team/`.

## To add a client logo
Add an object to `clients.json`. Add logo SVG to `public/images/clients/`. Keep logos grayscale-safe.
