# M10 Website — Shayah LaCour

A Quarto website for the IBM6530 M10 assignment, published to GitHub Pages.

## File Structure

```
M10/
├── _quarto.yml          ← site config, navbar, footer
├── custom.scss          ← site-wide styles
├── index.qmd            ← Home page (photo, bio, skills, education)
├── dashboard.qmd        ← Quarto Dashboard (attribution analysis)
├── shiny-essay.qmd      ← Essay: Building Shiny Apps
├── shinylive-essay.qmd  ← Essay: What is Shinylive?
├── docs/                ← rendered output (auto-generated, push this to GitHub)
└── README.md            ← this file
```

## Local Rendering

```bash
# Render the whole site
quarto render

# Preview with live reload
quarto preview
```

Output goes to `docs/`. Open `docs/index.html` in a browser to verify.

## Publishing to GitHub Pages

### First time setup

1. Create a new GitHub repo (e.g. `m10-website`)
2. Push this entire folder:

```bash
git init
git add .
git commit -m "Initial site"
git remote add origin https://github.com/YOUR_USERNAME/m10-website.git
git push -u origin main
```

3. In GitHub → Settings → Pages:
   - Source: **Deploy from a branch**
   - Branch: `main` / folder: `/docs`
   - Click Save

4. Your site will be live at `https://YOUR_USERNAME.github.io/m10-website/`

### Subsequent updates

```bash
quarto render
git add .
git commit -m "Update content"
git push
```

GitHub Pages rebuilds automatically after each push.

## Publishing to Quarto Pub

```bash
quarto publish quarto-pub
```

Follow the prompts to authenticate and choose a slug. The site will be at `https://YOUR_USERNAME.quarto.pub/m10-website/`.

## Notes

- `eval: false` is set globally in `_quarto.yml` — the dashboard uses its own `echo: false` 
  and the eval flag only applies to the essay code chunks (which are intentionally 
  shown as examples, not executed).
- The `dashboard.qmd` file uses the Quarto Dashboard format (introduced in Quarto 1.4+). 
  Make sure your Quarto version is up to date: `quarto --version`
- Place any data files (e.g. `knc_attribution.csv`) in this folder so the dashboard 
  can reference them with a relative path.
