# zero-jargon.github.io

Single-page site for **0J Consulting Oy**. Pure black, glitchy ANSI aesthetic,
no menus, no navigation — one page.

Hosted on GitHub Pages at <https://zero-jargon.github.io>, later moving to
<https://0j.fi>.

## Structure

```
.
├── index.html                 # the page
├── favicon.ico                # multi-res favicon
├── robots.txt / sitemap.xml   # crawler hints
├── .nojekyll                  # tell GitHub Pages to serve files as-is
└── assets/
    ├── css/style.css
    └── images/
        ├── h7-zerojargon.png              # ANSI hero art (640x400)
        ├── h7-zerojargon_glitchy_square.jpg  # square logo (815x815, source)
        ├── footer-logo.jpg                # optimized footer mark
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

## Deploy to GitHub Pages

1. Commit and push to the `main` branch of the `zero-jargon/zero-jargon.github.io` repo:

   ```bash
   git add .
   git commit -m "Publish 0J Consulting site"
   git push origin main
   ```

2. In the repo on GitHub: **Settings → Pages**.
   - **Source:** `Deploy from a branch`
   - **Branch:** `main` / `root`
   - Save.

3. Because the repo is named `zero-jargon.github.io`, it publishes at the root:
   <https://zero-jargon.github.io> (allow a minute or two for the first build).

## Custom domain (0j.fi) — later

When you're ready to move to `0j.fi`:

1. Create a file named `CNAME` in the repo root containing a single line:

   ```
   0j.fi
   ```

   (Or set it under **Settings → Pages → Custom domain**, which creates the file for you.)

2. At your DNS provider, point the domain at GitHub Pages:
   - **Apex `0j.fi`** — four `A` records:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
     (and the matching `AAAA` records if you want IPv6).
   - **`www.0j.fi`** — a `CNAME` to `zero-jargon.github.io`.

3. Back in **Settings → Pages**, tick **Enforce HTTPS** once the certificate is issued.

> Note: all asset paths in `index.html` are root-absolute (`/assets/...`),
> so they work identically on `zero-jargon.github.io` and `0j.fi`.
