# Savanna Myer — Portfolio Site

Personal brand and resume site for Savanna Myer, Head of Security & Compliance.

**Live site:** https://savanna.myersmiles.com

## Repository Contents

| File | Description | Size |
|------|-------------|------|
| `index.html` | Self-contained portfolio site | ~3.9MB |
| `savanna-myer-detailed-resume.pdf` | 10-page detailed resume with glossary | ~30KB |
| `savanna-myer-summary.pdf` | 8-page infographic summary | ~21KB |
| `savanna-myer-ats.txt` | ATS-scannable plain text (government/federal) | ~5KB |
| `og-preview.jpg` | Social media preview image — **add before going live** | 1200×630px |
| `CNAME` | Custom domain config for GitHub Pages | 1 line |

## Deployment

Hosted via **GitHub Pages** on a custom domain.

```
Branch: main
Source: / (root)
Custom domain: savanna.myersmiles.com
HTTPS: enforced
```

DNS: Add a `CNAME` record pointing `savanna` → `jessemyer.github.io`

## Tech Stack

- Pure HTML/CSS/JS — no build tools, no framework, no npm
- D3.js for data visualizations (radar, area charts, venn diagram, dumbbell chart)
- Google Fonts: Cormorant Garamond, Jost, DM Mono
- All images base64-embedded — fully self-contained single file
- PDF documents: ReportLab (Python), Times/Helvetica/Courier typography

## Updating Resume Files

Drop new PDF/TXT files in the root, commit, and push.
GitHub Pages auto-deploys in ~2 minutes.

```bash
git add savanna-myer-detailed-resume.pdf
git commit -m "docs: update detailed resume"
git push
```

## Updating Site Content

The site is generated from `/build_v29.py` (not checked in — lives locally).
To regenerate: run `python3 build_v29.py` then copy the output to `index.html`.

## Updating Recommendations

Search `index.html` for placeholder names:
- Alex Thornton, Jordan Mercer, Dana Whitfield
- Priya Nambiar, Marcus Delacroix, Soren Lindqvist

Replace name, role title, and testimonial text in the `.rec-card` blocks.

## Contact Form

Currently uses `mailto:`. To connect to Formspree:
1. Sign up at formspree.io, create a form, get the endpoint URL
2. In `index.html`, find `doSubmit()` and replace the `mailto:` line with a `fetch()` POST to the Formspree endpoint

## Adding og-preview.jpg

Screenshot the hero section at 1200×630px and save as `og-preview.jpg` in the root.
This image appears when the site is shared on LinkedIn, Twitter/X, Slack, etc.
The `<meta property="og:image">` tag already references it.
