# Sunyoung Seo — Portfolio

Static one-page portfolio built from `sunyoung_portfolio.pdf`. No build step — a single
self-contained `index.html` with inline CSS, styled to match <https://onghwan.github.io/>.

```
index.html          ← all markup and CSS
.nojekyll
assets/
  img/              ← imagery extracted from the PDF at native resolution
  sunyoung_portfolio.pdf
```

## Preview locally

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Deploy to GitHub Pages

Option A — a **project site** at `https://<user>.github.io/sunyoung-portfolio`:

```bash
git init && git add -A && git commit -m "Portfolio site"
git branch -M main
git remote add origin https://github.com/<user>/sunyoung-portfolio.git
git push -u origin main
```

Then in the repo: **Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)`**.

Option B — a **user site** at `https://<user>.github.io`: create a repo named exactly
`<user>.github.io` and push these files to its `main` branch.

`.nojekyll` is included so GitHub Pages serves the files as-is.

## Editing

- Everything lives in `index.html`. Each project is one `<section class="project">`:
  an `<h2>`, a `.meta` line, a `.shots` strip of screenshots, then `.prose` paragraphs.
- Colors are CSS variables at the top of the `<style>` block, with a
  `prefers-color-scheme: dark` override right below.
- `.shots` is a horizontally scrolling strip. Images are sized by height, so portrait
  and landscape can be mixed freely; add `class="wide"` to landscape images for a
  smaller corner radius.
- To add a screenshot, drop a JPEG into `assets/img/` and add an `<img>` to the strip:
  `sips -Z 1000 -s format jpeg -s formatOptions 70 --out assets/img/new.jpg source.png`
- Unused spares extracted from the PDF, kept in case they are wanted later:
  `about-photo.jpg` (ideation session), `ces-logo.png`, `hero-3.jpg`.
- The header and footer both link to `assets/sunyoung_portfolio.pdf`. Delete that file
  and the two "Portfolio (PDF)" links if the PDF should not be public.
