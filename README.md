# 0j.fi

Single-page site for **0J Consulting Oy** — a Finnish cyber security consultancy
(CTI, DFIR, malware analysis). Pure black, glitchy ANSI aesthetic, no menus,
no navigation — one page.

Served from GitHub Pages (repo `zero-jargon/zero-jargon.github.io`) on the
custom domain **<https://0j.fi>**.

## Structure

```
.
├── index.html                 # the page
├── CNAME                       # custom domain (0j.fi) for GitHub Pages
├── favicon.ico                # multi-res favicon
├── robots.txt / sitemap.xml   # crawler hints (point at https://0j.fi/)
├── .nojekyll                  # tell GitHub Pages to serve files as-is
└── assets/
    ├── css/style.css
    └── images/
        ├── h7-zerojargon.png                 # ANSI hero art (640x400)
        ├── h7-zerojargon_glitchy_square.jpg  # square logo (815x815, source)
        ├── footer-logo.jpg                   # optimized footer mark
        ├── apple-touch-icon.png
        ├── favicon-32.png
        └── favicon-16.png
```

## Local preview

Any static server works. For example:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploy

Changes go live by pushing to `main`:

```bash
git add .
git commit -m "Update site"
git push origin main
```

GitHub Pages rebuilds automatically (watch the **Actions** tab). Pages config:
**Settings → Pages → Source: Deploy from a branch → `main` / root**.

## Domain & DNS (live)

The site is on the custom domain `0j.fi`, configured via:

- **`CNAME`** file in the repo root containing `0j.fi`.
- **DNS** at the registrar:
  - Apex `0j.fi` → four `A` records:
    `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
    (plus matching `AAAA` records for IPv6, if used).
  - `www.0j.fi` → `CNAME` to `zero-jargon.github.io`.
- **Settings → Pages → Enforce HTTPS** enabled once the certificate is issued.

GitHub 301-redirects `zero-jargon.github.io` → `0j.fi`, so the old URL keeps working.

## SEO notes

- All absolute URLs (canonical, Open Graph, Twitter card, JSON-LD) point at
  `https://0j.fi/`. If the domain ever changes, update them in `index.html`,
  `robots.txt`, and `sitemap.xml`.
- Structured data (`ProfessionalService` JSON-LD) describes the company and
  services; it deliberately contains **no email** to keep addresses out of the
  raw HTML (emails are shown on-page in `name [at] 0j.fi` form for the same
  reason).
- After go-live: verify the domain in **Google Search Console** and submit
  `sitemap.xml`.

> Note: all in-page asset paths are root-absolute (`/assets/...`), so they work
> regardless of which domain serves the site.
