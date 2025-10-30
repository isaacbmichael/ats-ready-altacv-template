<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <title>ATS-Ready altacv Resume Template — README</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    :root {
      --ink:#222;
      --muted:#5b6470;
      --card:#fafafa;
      --rule:#e7e7e7;
      --link:#0a66c2;
    }
    html,body{margin:0;padding:0}
    body{
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, "Apple Color Emoji","Segoe UI Emoji", "Segoe UI Symbol";
      line-height:1.6; color:var(--ink); background:#fff;
    }
    .container{max-width:900px; margin:40px auto; padding:0 20px;}
    h1{font-size:2rem; margin:.25rem 0 1rem;}
    h2{margin:2rem 0 0.75rem; font-size:1.35rem}
    p{margin:0.6rem 0}
    ul{margin:0.4rem 0 0.8rem 1.25rem}
    li{margin:0.25rem 0}
    blockquote{
      border-left:4px solid var(--rule);
      padding:.6rem .9rem; margin:1rem 0; background:var(--card); color:var(--ink);
    }
    code, pre{font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, "Liberation Mono", monospace; font-size:.95em;}
    code{background:#f4f6f8; padding:.15em .35em; border-radius:.35rem}
    pre{background:#0b1020; color:#e6edf3; padding:1rem; overflow:auto; border-radius:.6rem}
    pre code{background:transparent; padding:0}
    hr{border:0; border-top:1px solid var(--rule); margin:1.5rem 0}
    a{color:var(--link); text-decoration:none}
    a:hover{text-decoration:underline}
    .badge{display:inline-block; vertical-align:middle}
    .meta{color:var(--muted)}
  </style>
</head>
<body>
  <main class="container">
    <h1>ATS-Ready altacv Resume Template</h1>

    <p><strong>A single-column LaTeX resume that <em>looks</em> like two columns, with an ATS mode that exports a clean text layer (icons silenced, smart dashes normalized) and a showcase mode with an optional logo.</strong></p>

    <blockquote>
      <strong>Assumptions (template):</strong>
      Engine = pdfLaTeX <em>or</em> XeTeX/LuaTeX • Class = <code>altacv</code> • Paper = A4 • Faux 2-column rail (year gutter 7%) • Icons via FontAwesome • ATS toggle = off by default
    </blockquote>

    <p>
      <img class="badge" alt="License" src="https://img.shields.io/badge/license-MIT-blue.svg" />
    </p>

    <hr />

    <h2>✨ Features</h2>
    <ul>
      <li><strong>ATS toggle</strong>: Uncomment <code>\ATStrue</code> to hide photo, switch <em>Technical Skills</em> to single-column, and normalize <code>–</code>/<code>—</code> in the PDF text layer.</li>
      <li><strong>Faux 2-column Experience</strong>: True single column for ATS; visually mimics two columns with a <strong>year gutter</strong> + <strong>right content rail</strong>.</li>
      <li><strong>Icon-silent extraction</strong>: Icons appear visually, while <code>ActualText</code> exposes clean, searchable labels (e.g., <code>Email: ... |</code>).</li>
      <li><strong>Logo / No-logo</strong>: Independent <code>\LOGOtrue</code> toggle; ATS mode forces it off for conservative parsing.</li>
      <li><strong>Aligned sub-roles</strong>: <code>ExpSubRole</code> (inside the entry) and <code>ExpRightRail</code> (outside the entry) keep headers/bullets perfectly aligned with the role/title rail.</li>
      <li><strong>Templated Skills</strong>: Product-agnostic placeholders for both ATS (single-column) and Showcase (3-column) modes.</li>
      <li><strong>Dash normalization</strong>: En-dash→<code>-</code>, Em-dash→<code>--</code> in the text layer; visual glyphs remain unchanged.</li>
      <li><strong>Unicode &amp; extraction-safe</strong>: <code>glyphtounicode</code> and <code>\pdfgentounicode=1</code> (pdfLaTeX path) plus <code>accsupp</code> wrappers for reliable copy/paste and ATS parsing.</li>
    </ul>

    <h2>📌 Latest Highlights (2025-10-29)</h2>
    <ul>
      <li>Added <strong><code>ExpRightRail</code></strong> to align any post-entry sub-roles with the main rail.</li>
      <li>Masked <strong>Technical Skills</strong> to be template-ready in both ATS and Showcase modes.</li>
      <li>README + CI scaffold for building <strong>both PDFs</strong> (showcase + ATS) automatically.</li>
    </ul>

    <h2>📊 Example Outputs</h2>
    <ul>
      <li><strong>Showcase PDF:</strong> <code>template.pdf</code></li>
      <li><strong>ATS PDF:</strong> <code>resume-ats.pdf</code></li>
    </ul>

    <p class="meta"><em>Direct downloads:</em>
      <a href="https://github.com/isaacbmichael/ats-ready-altacv-template/releases/latest/download/template.pdf">template.pdf</a>
      &nbsp;•&nbsp;
      <a href="https://github.com/isaacbmichael/ats-ready-altacv-template/releases/latest/download/resume-ats.pdf">resume-ats.pdf</a>
    </p>

    <blockquote>
      <strong>Tip:</strong> If your logo file isn’t present, either add <code>assets/globe_high.png</code> (or change <code>\PhotoPath</code>) <em>or</em> comment out the <code>\photoR{...}{\PhotoPath}</code> line to avoid a missing-file warning.
    </blockquote>

    <h2>🚀 Quick Start</h2>
    <pre><code># Build (showcase)
latexmk -pdf template.tex

# Build ATS version (uncomment ATStrue on the fly)
sed 's/^%\\ATStrue/\\ATStrue/' template.tex &gt; template-ats.tex
latexmk -pdf -jobname=resume-ats template-ats.tex
</code></pre>

    <h3>Optional: GitHub Actions</h3>
    <p>A ready-to-use workflow is included at <code>.github/workflows/build.yml</code>. On each push it installs TeX Live, builds both PDFs, and publishes them as artifacts.</p>

    <hr />

    <h2>📂 Repository Contents</h2>
    <ul>
      <li><code>template.tex</code> — the main resume template (ATS toggle, faux 2-col rail, alignment helpers).</li>
      <li><code>assets/</code> — optional images (e.g., <code>globe_high.png</code>).</li>
      <li><code>.github/workflows/build.yml</code> — CI to build and upload PDFs.</li>
      <li><code>Makefile</code> — convenience targets: <code>showcase</code>, <code>ats</code>, <code>all</code>, <code>clean</code>.</li>
      <li><code>LICENSE</code> — MIT license.</li>
      <li><code>README.md</code> — this file.</li>
    </ul>

    <hr />

    <h2>🧭 Glossary</h2>
    <ul>
      <li><strong>ATS (Applicant Tracking System):</strong> Software that ingests resume text; sensitive to multi-column layouts, images, icons, and Unicode quirks.</li>
      <li><strong>ActualText:</strong> A PDF accessibility feature used here to show icons visually but export clean field labels in the text layer.</li>
      <li><strong>Faux 2-column rail:</strong> Single-column document with a fixed <strong>year gutter (7%)</strong> and a <strong>right content rail</strong> for reliable parsing.</li>
      <li><strong><code>ExpSubRole</code> / <code>ExpRightRail</code>:</strong> Macros to format sub-roles either inside the <code>ExpEntry</code> block or afterward while keeping perfect alignment.</li>
      <li><strong>Dash normalization:</strong> Maps <code>–</code>→<code>-</code> and <code>—</code>→<code>--</code> for ATS while preserving typographic dashes visually.</li>
    </ul>

    <hr />

    <h2>⚙️ Customization Guide</h2>
    <p>Edit variables near the bottom of <code>template.tex</code>:</p>
    <pre><code>\newcommand{\FullName}{Your Name}
\newcommand{\RoleTagline}{Your Role Tagline (e.g., Data \&amp; Services Leader)}
\newcommand{\Email}{you@example.com}
\newcommand{\Phone}{000-000-0000}
\newcommand{\LinkedInHandle}{your-handle}
\newcommand{\PortfolioURL}{example.com}
\newcommand{\LocationName}{City, ST}
\newcommand{\LocationURL}{https://www.google.com/maps/search/?api=1&amp;query=City}
</code></pre>
    <p><strong>Escape special characters</strong> in header fields: <code>&amp;</code>→<code>\&amp;</code>, <code>%</code>→<code>\%</code>, <code>#</code>→<code>\#</code>, <code>_</code>→<code>\_</code>.</p>

    <hr />

    <h2>🧩 Troubleshooting</h2>
    <ul>
      <li><strong>Undefined icon (e.g., <code>\faMapMarker</code>):</strong> Ensure your <code>altacv</code>/FontAwesome setup is present. Some setups prefer <code>\faMapMarker*</code>.</li>
      <li><strong>Weird line breaks:</strong> <code>\sloppy</code> and <code>\emergencystretch</code> help. Long URLs can still cause overfull boxes; this is cosmetic in most cases.</li>
      <li><strong>Minipage page breaks:</strong> The right-rail is a <code>minipage</code>, which doesn’t break across pages. Keep entries concise or split long sections.</li>
    </ul>

    <hr />

    <h2>⚠️ Disclaimer</h2>
    <p>This template is provided “as is” under the MIT License with no warranty of any kind.
      ATS behavior varies by vendor and configuration; <strong>compatibility isn’t guaranteed</strong>.
      Please validate your generated PDF against the specific ATS you’ll submit to.</p>
    <p>This project is not affiliated with or endorsed by AltaCV, Font Awesome, GitHub,
      or any ATS vendor. All trademarks and product names are the property of their respective owners.</p>

    <hr />

    <h2>🙏 Credits</h2>
    <p>Built on the excellent <a href="https://github.com/liantze/AltaCV">AltaCV class by LianTze Lim</a>.</p>

    <hr />

    <p class="meta">© 2025 Isaac B. Michael •
      <a href="mailto:isaac.b.michael@gmail.com">Email</a> •
      <a href="https://www.linkedin.com/in/isaacbmichael">LinkedIn</a> •
      <a href="https://github.com/isaacbmichael">GitHub</a>
    </p>
  </main>
</body>
</html>

---

© 2025 Isaac B. Michael • [Email](mailto:isaac.b.michael@gmail.com) • [LinkedIn](https://www.linkedin.com/in/isaacbmichael) • [GitHub](https://github.com/isaacbmichael)
