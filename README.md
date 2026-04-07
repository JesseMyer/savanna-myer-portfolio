# savanna-myer-portfolio

Personal brand site and professional documents for **Savanna Myer** — Head of Security, Compliance & Governance.

Live: [savanna.myersmiles.com](https://savanna.myersmiles.com)

---

## What's in this repo

| File | Description |
|------|-------------|
| `index.html` | Single-file portfolio site (self-contained, ~10MB with embedded assets) |
| `savanna-myer-detailed-resume.docx` | 22-page detailed resume, Word format |
| `savanna-myer-detailed-resume.doc` | Word 97-2003 format (maximum compatibility) |
| `savanna-myer-summary.pdf` | 3-page premium PDF summary |
| `savanna-myer-ats.txt` | Plain-text ATS-optimized resume |

---

## Site (`index.html`)

A single self-contained HTML file deployed via GitHub Pages. No build step, no dependencies, no CDN calls at runtime. Everything — fonts, images, icons, the headshot — is embedded as base64 or inlined CSS.

**Sections:**
- Identity and value proposition with animated KPI strip
- Professional summary and Coordinated Compliance methodology
- Career timeline (Rubrik → People.ai → Elastic → Foundation Era)
- Certification portfolio: 22 active standards, 9 jurisdictions
- Global market access map: certification to revenue mapping
- Myers Miles photography section (community work with SCDA and COMSCC)
- Contact and document downloads

**Tech:**
- Vanilla HTML/CSS/JS — no frameworks
- D3.js for data visualizations
- Cormorant Garamond (display) + Jost (sans) via Google Fonts
- Dark navy / teal / amber color system matching `--teal: #3ab5d4`, `--amber: #c8921a`
- Responsive: mobile, tablet, desktop
- GitHub Pages deployment via `jessemyer/savanna-myer-portfolio`
- Custom domain via Squarespace CNAME: `savanna` → `jessemyer.github.io`

---

## Detailed Resume (`savanna-myer-detailed-resume.docx` / `.doc`)

Built with `docx-js` (Node.js), post-processed with a Python patcher for full Word compatibility.

**22 pages covering:**

| Page | Section |
|------|---------|
| P1 | Identity, Professional Summary, 6 KPI tiles |
| P2 | Index (2-column with dotted leaders) |
| P3 | Core Competencies (10 domains) |
| P4 | Certification & Standards Portfolio: 22 Active Standards |
| P5 | Career Overview: 13 Years, Three Arcs |
| P6 | Rubrik, Inc. (Head of Security, Compliance & Governance) |
| P7 | People.ai (Sr. Manager, Governance & Compliance) |
| P8 | Elastic (Principal Security Risk & Compliance Analyst) |
| P9 | Aetna / CVS Health |
| P10 | Evariant |
| P11 | Earlier Roles: Foundation Era 2011–2018 (Saint Mary's + OSU/Huntington) |
| P12 | Customer Trust: Function Overview |
| P13 | Education (4 degrees) |
| P14 | Interdisciplinary Foundation: Three Degrees, One Lens |
| P15 | Compliance Culture & Change Management |
| P16 | Client & Industry Experience Breakdown |
| P17 | Global Market Access, Certification to Revenue Mapping |
| P18 | Technology & Tool Proficiency |
| P19 | Professional Development & Continuing Education |
| P20 | Professional Memberships & Affiliations |
| P21 | Appendix A: Certification Acquisition Timeline |
| P22 | Appendix B: Program Performance Metrics |

**Design system:**
- Colors: Website teal `#2a9db8` (primary), Navy `#1a4a7a` (secondary), Win green `#2d8a55` (positive metrics)
- Fonts: Cormorant Garamond (display headings), Century Gothic (body and sidebar)
- All borders ≤ 0.25pt (hairline only)
- Sidebar: tools, key terms, contextual items for every career block
- `richBullet()` bolds 40 sidebar/glossary cross-reference terms inline in every bullet
- Headshot embedded as base64 JPEG on P1

**Build pipeline:**
```bash
node build_resume_v9.js
# Outputs: savanna-myer-detailed-resume.docx
# Post-build: patch_docx.py injects theme1.xml, webSettings.xml,
#             Normal style, DefaultParagraphFont (all required by Word,
#             all omitted by docx-js)
```

**Word compatibility notes:**
- `docx-js` does not generate `word/theme/theme1.xml` or `word/webSettings.xml`; Word hard-requires both. `patch_docx.py` injects them using Python's `zipfile` module after every build.
- `Normal` paragraph style (with `w:default="1"`) and `DefaultParagraphFont` character style are also injected; their absence causes the "unreadable content" error in Word 2016+.
- All `tintCell()` returns are wrapped in `tintRow()` before being pushed to the document body. A bare `<w:tc>` as a direct child of `<w:body>` is a hard XML schema violation that Word rejects silently.
- For maximum compatibility, use the `.doc` file (Word 97-2003 binary format, converted by LibreOffice).

---

## PDF Summary (`savanna-myer-summary.pdf`)

3-page premium PDF built with ReportLab canvas (Python), pixel-exact layout. No PDF template or intermediate format.

**Page 1:** Identity (headshot + contact + credentials + education + memberships) · Tagline · 6 KPI tiles · Why Hire Me narrative · What I Build (4 proof points with financial figures)

**Page 2:** Financial Impact sidebar (6 figures: $1B+, $5.6B, $1.2B, +$18M, $271M, $100B+) · Program Metrics sidebar (8 before/after rows) · Target Role · Full career timeline (4 eras with colored financial impact tags) · Coordinated Compliance methodology strip (5 Greek-letter pillars)

**Page 3:** Certification portfolio (22 standards, 3-column grid with market access justification per cert) · Coordinated Compliance methodology strip · Professional Development (6 programs) · Pull quote

**Design matches the site:** same navy/teal/amber palette, same two-column sidebar structure, headshot top-left of sidebar.

---

## ATS Text (`savanna-myer-ats.txt`)

Plain UTF-8, no special characters, structured for automated resume parsers. Includes full contact info, summary, all career blocks with dates and bullets, certifications list, education, tools. ~11KB, 152 lines.

---

## Key content facts

- **Location:** Connecticut, United States (remote-first)
- **Phone:** 614-309-4272
- **Email:** savanna.myer@gmail.com
- **LinkedIn:** linkedin.com/in/savannamyer
- **Portfolio:** savanna.myersmiles.com
- **FedRAMP posture:** "assisted in building" — never "led" (accurate per role scope)
- **References:** available upon request (no references page in document set)

---

## Repo structure

```
savanna-myer-portfolio/
├── index.html                          # Full site (single file, ~10MB)
├── savanna-myer-detailed-resume.docx   # 22-page detailed resume
├── savanna-myer-detailed-resume.doc    # Word 97-2003 (max compatibility)
├── savanna-myer-summary.pdf            # 3-page PDF summary
├── savanna-myer-ats.txt               # ATS plain text
└── README.md                           # This file
```

---

## Build sources

All builders live outside this repo (working directory only). For regeneration:

| Builder | Language | Output |
|---------|----------|--------|
| `build_v34.py` | Python | `index.html` (site) |
| `build_resume_v9.js` | Node.js + docx-js | `savanna-myer-detailed-resume.docx` |
| `patch_docx.py` | Python + zipfile | Word compatibility patch (runs after v9.js) |
| `build_pdf_premium.py` | Python + ReportLab | `savanna-myer-summary.pdf` |
| `build_ats.py` | Python | `savanna-myer-ats.txt` |

DOC conversion (LibreOffice):
```bash
soffice --headless --convert-to doc --outdir ./ savanna-myer-detailed-resume.docx
```

---

## Deployment

GitHub Pages is enabled on this repo, serving from the `main` branch root.

DNS: Squarespace domain `myersmiles.com` has a CNAME record:
```
savanna  →  jessemyer.github.io
```

The site resolves at `https://savanna.myersmiles.com`. No `_config.yml` or Jekyll configuration; GitHub Pages serves `index.html` directly.
