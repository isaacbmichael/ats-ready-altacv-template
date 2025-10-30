# ATS-Ready altacv Resume Template

**A single-column LaTeX resume that *looks* like two columns, with an ATS mode that exports a clean text layer (icons silenced, smart dashes normalized) and a showcase mode with an optional logo.**

> **Assumptions (template):** Engine = pdfLaTeX *or* XeTeX/LuaTeX • Class = `altacv` • Paper = A4 • Faux 2-column rail (year gutter 7%) • Icons via FontAwesome • ATS toggle = off by default

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Build](https://github.com/isaacbmichael/ats-ready-altacv-template/actions/workflows/build.yml/badge.svg)
![Release](https://img.shields.io/github/v/release/isaacbmichael/ats-ready-altacv-template?include_prereleases&label=release)

---

## ✨ Features
- **ATS toggle**: Uncomment `\ATStrue` to hide photo, switch *Technical Skills* to single-column, and normalize `–`/`—` in the PDF text layer.
- **Faux 2-column Experience**: True single column for ATS; visually mimics two columns with a **year gutter** + **right content rail**.
- **Icon-silent extraction**: Icons appear visually, while `ActualText` exposes clean, searchable labels (e.g., `Email: ... |`).
- **Logo / No-logo**: Independent `\LOGOtrue` toggle; ATS mode forces it off for conservative parsing.
- **Aligned sub-roles**: `ExpSubRole` (inside the entry) and `ExpRightRail` (outside the entry) keep headers/bullets perfectly aligned with the role/title rail.
- **Templated Skills**: Product-agnostic placeholders for both ATS (single-column) and Showcase (3-column) modes.
- **Dash normalization**: En-dash→`-`, Em-dash→`--` in the text layer; visual glyphs remain unchanged.
- **Unicode & extraction-safe**: `glyphtounicode` and `\pdfgentounicode=1` (pdfLaTeX path) plus `accsupp` wrappers for reliable copy/paste and ATS parsing.

---

## 📌 Latest Highlights (2025-10-30)
- Added **`ExpRightRail`** to align any post-entry sub-roles with the main rail.
- Masked **Technical Skills** to be template-ready in both ATS and Showcase modes.
- CI note: the provided workflow now builds **one** PDF (Showcase *or* ATS) based on `\ATStrue`.

---

## 📊 Example Outputs

**Direct downloads (Release assets)**
- **Showcase PDF:** [`template.pdf`](https://github.com/isaacbmichael/ats-ready-altacv-template/releases/latest/download/template.pdf)  
- **ATS PDF:** [`resume-ats.pdf`](https://github.com/isaacbmichael/ats-ready-altacv-template/releases/latest/download/resume-ats.pdf)

**Mobile-friendly mirrors (GitHub Pages)**
- **Showcase PDF:** [`template.pdf`](https://isaacbmichael.github.io/assets/pdfs/template.pdf)  
- **ATS PDF:** [`resume-ats.pdf`](https://isaacbmichael.github.io/assets/pdfs/resume-ats.pdf)

> **Tip:** If your logo file isn’t present, either add `assets/globe_high.png` (or change `\PhotoPath`) *or* comment out the `\photoR{...}{\PhotoPath}` block to avoid a missing-file warning.

---

## 🚀 Quick Start

```bash
# Build (showcase)
latexmk -pdf template.tex

# Build ATS version (uncomment ATStrue on the fly)
sed 's/^%\\ATStrue/\\ATStrue/' template.tex > template-ats.tex
latexmk -pdf -jobname=resume-ats template-ats.tex
```

### Optional: GitHub Actions
A ready-to-use workflow is included at `.github/workflows/build.yml`. On each push it installs TeX Live, builds both PDFs, and publishes them as artifacts.

---

## 📂 Repository Contents
- `template.tex` — the main resume template (ATS toggle, faux 2-col rail, alignment helpers).
- `assets/` — optional images (e.g., `globe_high.png`).
- `.github/workflows/build.yml` — CI to build and upload PDFs.
- `Makefile` — convenience targets: `showcase`, `ats`, `all`, `clean`.
- `LICENSE` — MIT license.
- `README.md` — this file.

---

## 🧭 Glossary
- **ATS (Applicant Tracking System):** Software that ingests resume text; sensitive to multi-column layouts, images, icons, and Unicode quirks.
- **ActualText:** A PDF accessibility feature used here to show icons visually but export clean field labels in the text layer.
- **Faux 2-column rail:** Single-column document with a fixed **year gutter (7%)** and a **right content rail** for reliable parsing.
- **`ExpSubRole` / `ExpRightRail`:** Macros to format sub-roles either inside the `ExpEntry` block or afterward while keeping perfect alignment.
- **Dash normalization:** Maps `–`→`-` and `—`→`--` for ATS while preserving typographic dashes visually.

---

## ⚙️ Customization Guide
Edit variables near the bottom of `template.tex`:

```latex
\newcommand{\FullName}{Your Name}
\newcommand{\RoleTagline}{Your Role Tagline (e.g., Data \& Services Leader)}
\newcommand{\Email}{you@example.com}
\newcommand{\Phone}{000-000-0000}
\newcommand{\LinkedInHandle}{your-handle}
\newcommand{\PortfolioURL}{example.com}
\newcommand{\LocationName}{City, ST}
\newcommand{\LocationURL}{https://www.google.com/maps/search/?api=1&query=City}
```

**Escape special characters** in header fields: `&`→`\&`, `%`→`\%`, `#`→`\#`, `_`→`\_`.

---

## 🧩 Troubleshooting
- **Undefined icon (e.g., `\faMapMarker`):** Ensure your `altacv`/FontAwesome setup is present. Some setups prefer `\faMapMarker*`.
- **Weird line breaks:** `\sloppy` and `\emergencystretch` help. Long URLs can still cause overfull boxes; this is cosmetic in most cases.
- **Minipage page breaks:** The right-rail is a `minipage`, which doesn’t break across pages. Keep entries concise or split long sections.

---

## ⚠️ Disclaimer
This template is provided “as is” under the MIT License with no warranty of any kind.  
ATS behavior varies by vendor and configuration; **compatibility isn’t guaranteed**.  
Please validate your generated PDF against the specific ATS you’ll submit to.

This project is not affiliated with or endorsed by AltaCV, Font Awesome, GitHub, or any ATS vendor. All trademarks and product names are the property of their respective owners.

---

© 2025 Isaac B. Michael • [Email](mailto:isaac.b.michael@gmail.com) • [LinkedIn](https://www.linkedin.com/in/isaacbmichael) • [GitHub](https://github.com/isaacbmichael)
