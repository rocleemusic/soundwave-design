# Public Assets

Static files served as-is. Not processed by Astro.

| Folder | What goes here |
|--------|---------------|
| `images/portfolio/` | Project cover images (16:9, prefer WebP/AVIF) |
| `images/blog/` | Blog post cover images |
| `images/team/` | Team member headshots |
| `images/clients/` | Client logos (SVG preferred, grayscale-safe) |
| `images/facility/` | Studio/gear/room photography |
| `media/audio/` | Short audio samples for portfolio entries |
| `media/video/` | Short video samples (long-form embeds go via SoundCloud/YouTube) |
| `favicon*` | Favicon files (ico, png, svg, webmanifest) |

## Notes
- No autoplay audio anywhere
- Video: self-host short clips only. Long-form → YouTube/SoundCloud lite-embed
- Images: always supply `width` and `height` attributes to prevent layout shift
