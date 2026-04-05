# GitHub Setup — Savanna Myer Portfolio
# New repo: jessemyer/savanna-myer-portfolio
# Run these commands from the folder containing these files

================================================================================
STEP 1 — CREATE REPO ON GITHUB
================================================================================
Go to: https://github.com/new

  Repository name:  savanna-myer-portfolio
  Visibility:       Public  (required for free GitHub Pages)
  Initialize:       NO (we have files already)

Click "Create repository" — GitHub will show you a URL like:
  https://github.com/jessemyer/savanna-myer-portfolio


================================================================================
STEP 2 — PUSH THESE FILES
================================================================================
Open terminal in this folder and run:

  git init
  git add .
  git commit -m "feat: launch Savanna Myer portfolio site v1.0"
  git branch -M main
  git remote add origin https://github.com/jessemyer/savanna-myer-portfolio.git
  git push -u origin main


================================================================================
STEP 3 — ENABLE GITHUB PAGES
================================================================================
Go to: https://github.com/jessemyer/savanna-myer-portfolio/settings/pages

  Source:  Deploy from a branch
  Branch:  main  |  / (root)
  Click Save

Wait ~2 minutes. Test at:
  https://jessemyer.github.io/savanna-myer-portfolio/


================================================================================
STEP 4 — CONNECT CUSTOM DOMAIN
================================================================================
In GitHub Pages settings, enter:
  Custom domain: savanna.myersmiles.com

Then in your DNS provider (wherever myersmiles.com is registered):
  Type:   CNAME
  Name:   savanna
  Value:  jessemyer.github.io
  TTL:    Auto or 3600

Wait 5–60 minutes for DNS to propagate, then:
  ✓ Check "Enforce HTTPS" in GitHub Pages settings

Test: https://savanna.myersmiles.com


================================================================================
STEP 5 — VERIFY EVERYTHING WORKS
================================================================================
Open the site and check:
  ✓ Nav "DETAILED" button downloads savanna-myer-detailed-resume.pdf
  ✓ Nav "SUMMARY" button downloads savanna-myer-summary.pdf
  ✓ Nav "ATS" button downloads savanna-myer-ats.txt
  ✓ Contact section buttons do the same
  ✓ All 6 D3 visualizations load (radar, area charts, venn, dumbbell)
  ✓ Flag strip shows 8 country flags
  ✓ Typewriter animates in hero and contact

Test social sharing preview:
  https://cards-dev.twitter.com/validator
  Paste: https://savanna.myersmiles.com
  (Note: og-preview.jpg needed for image preview — add later)


================================================================================
WHAT TO DO NEXT
================================================================================
1. Screenshot the hero section at 1200×630px → save as og-preview.jpg
   → git add og-preview.jpg && git commit -m "feat: add social preview image" && git push

2. Replace placeholder recommendation names with real LinkedIn text
   → Edit index.html, search "Alex Thornton", replace all 6 rec cards

3. Connect contact form to Formspree (formspree.io — free tier available)
   → Get endpoint URL → replace mailto: line in doSubmit() function in index.html

4. Add Google Search Console
   → search.google.com/search-console → URL prefix → savanna.myersmiles.com
   → Verify via HTML file method (drop verification file in repo root, commit, push)
