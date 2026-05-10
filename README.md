# MixedDrive Lab — Website

Static website for **[mixeddrivelab.org](https://mixeddrivelab.org)** — an independent research initiative investigating perception, localization, and decision-making for autonomous systems operating in mixed-traffic environments.

## Stack

- Plain HTML + CSS — no build step, no JavaScript framework.
- Google Fonts (Fraunces, Source Sans 3, JetBrains Mono) loaded with `display=swap`.
- WebP assets with PNG fallback via `<picture>`.
- JSON-LD `ResearchOrganization` schema for SEO.

The site is fully self-contained and can be served from any static host (Apache, Nginx, Netlify, GitHub Pages, S3, etc.).

## Project structure

```
.
├── index.html              # Landing page
├── 404.html                # Custom error page
├── assets/
│   ├── logo-master.png     # 512x512 brand mark (PNG fallback)
│   └── logo-master.webp    # 512x512 brand mark (modern browsers)
├── apple-touch-icon.png    # 180x180 iOS home screen
├── favicon.ico             # Legacy multi-size favicon
├── favicon-16.png          # 16x16
├── favicon-32.png          # 32x32
├── og-image.png            # 1200x630 social card
├── robots.txt              # Crawler rules + AI-bot opt-out
├── sitemap.xml             # Search engine sitemap
├── security.txt            # RFC 9116 security contact
├── humans.txt              # /humans.txt convention
└── DEPLOY.md               # Hosting / cPanel deployment notes
```

## Local preview

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

Or any equivalent: `npx serve`, `caddy file-server`, etc.

## Deployment

Production hosting is currently on Rumahweb cPanel. See [DEPLOY.md](DEPLOY.md) for upload procedure, SSL setup, redirects, and post-deploy checklist.

## Versioning

[Semantic versioning](https://semver.org/). Releases are tagged on `main` (e.g. `v0.1.0`) and visible under [Releases](https://github.com/mixeddrivelab/mixeddrivelab-website/releases).

## Contact

`contact@mixeddrivelab.org`

---

© 2026 MixedDrive Lab. Independent research initiative — views expressed here do not represent any employer or affiliated institution.
