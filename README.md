# MBA Compensation Intelligence Framework (CIF)

**Full-Time MBA Program · David Eccles School of Business · University of Utah**

A single-file, browser-based decision tool that helps MBA students and career coaches evaluate job offers on their full economic value — not just base salary. Version 3.0.

---

## Live Link

**[Compensation Intelligence Framework (vG)]( https://coryjburk.github.io/compensation-intelligence-framework-vg/ )**

---

## What it is

The CIF is a self-contained HTML application (no server, no database, no build step). It bundles five interlocking tools for compensation strategy:

| Tool | What it answers |
|---|---|
| **Total Comp Calculator** | What is this offer actually worth beyond base salary? |
| **Cost-of-Living Normalizer** | Which offer wins after adjusting for city cost and taxes? |
| **Industry Heatmap** | How do industries compare on comp, growth, AI resilience, equity, and work-life? |
| **Offer Scorecard** | Which of two offers is the stronger long-term strategic choice? |
| **Skill Premium Index** | Which skills should I build to raise my market value? |

It also includes a coach-facing sidebar with session notes (saved in-browser), a strategic-framework quick reference, and a print/PDF export.

---

## ⚠️ Read this first: data provenance

**The numeric values in this tool are editorial estimates, not a live or verified dataset.**

The industry scores (0–100), skill premium scores, salary ranges, and cost-of-living indices were synthesized from general 2025–2026 market knowledge and publicly discussed benchmarks. They are **directional teaching aids**, not authoritative figures. Specifically:

- Industry and skill scores are **subjective composite assessments** assembled for instructional use. They are not computed from a named dataset and are not reproducible from a documented methodology.
- Salary ranges are **illustrative** and reflect broad market impressions, not current verified postings.
- Cost-of-living indices approximate commonly cited COL comparisons but are **not pulled from a maintained source**.
- The tool does **not** connect to Levels.fyi, Glassdoor, GMAC, NACE, the H1B database, or any API. Those platforms are listed inside the tool as **sources students should consult directly** for real figures.

**Implication for use:** treat CIF outputs as a structured way to *frame* a compensation conversation, not as evidence of what a specific role pays. Before any student acts on a number, they should verify it against a primary source. Values should be reviewed and updated at least annually (see [Maintenance](#maintenance)).

If you replace the built-in estimates with sourced figures, update this section to name the source and vintage.

---

## Quick start

1. Download `eccles-mba-cif-v3.html`.
2. Open it in any modern browser (Chrome, Edge, Safari, Firefox). It works offline.
3. That's it — there is nothing to install.

### Hosting options

| Method | How | Best for |
|---|---|---|
| **Share a link** | Upload to Google Drive / Box / Dropbox and share | Fastest, no web team |
| **Eccles web page** | Hand the single `.html` file to web services; drop at a path (e.g. `/mba/cif`) | Branded institutional URL |
| **Canvas / LMS** | Add as an External Tool / Redirect pointing at the hosted URL | Embedding in coursework |
| **GitHub Pages** | Commit the file; enable Pages on the repo | Version-controlled public hosting |

The file loads two external assets from CDNs (the Tabler icon font and the EB Garamond / DM Sans web fonts). If it must run fully offline or air-gapped, self-host those two assets and update the `<link>` tags. Without them the tool still functions — icons and custom fonts degrade gracefully.

---

## The five tools in detail

### 1. Total Compensation Calculator

Computes a **True Compensation Value (TCV)** from offer inputs:

```
TCV = ( Base + Bonus + Equity + Sign-On⁄3 + Retirement Match + Benefits ) × Brand Multiplier
```

- **Sign-on is amortized over 3 years** (divided by 3) to avoid overstating a one-time payment.
- **Brand multiplier** is a coarse tier adjustment (1.00–1.15) reflecting resume/optionality value. *This is a judgment lever, not a market measurement.*
- **Remote savings** are estimated at ~$5,200 per remote-day/week per year (commute + time). *Assumption, adjustable in code.*
- Outputs: TCV, effective hourly rate, remote savings, promotion-timeline label, and a component breakdown bar chart.

**Known limitation:** TCV mixes guaranteed cash, at-risk cash, illiquid equity, and a subjective brand factor into one number. It is a comparison heuristic, not a guaranteed-dollars figure. Coaches should say so when presenting it.

### 2. Cost-of-Living Normalizer

Adjusts two nominal offers to a common purchasing-power basis:

```
Purchasing-power value = Comp ÷ COL_index × 100
After-tax estimate     = Comp × (1 − top_marginal_state_rate)
```

- COL index baseline: US average = 100.
- Tax adjustment uses **top marginal state income tax only** — it ignores federal tax, local tax, brackets, deductions, and property/sales tax. It is a **rough** directional adjustment, not a tax calculation.

**Known limitation:** using the top marginal rate overstates the tax bite for most salaries. Read after-tax numbers as conservative, comparative, and approximate.

### 3. Industry Heatmap

Ranks 10 industries across five dimensions (Total Comp, Growth Trajectory, AI Resilience, Equity Upside, Work-Life Fit). Color intensity encodes the selected dimension's score. Clicking a cell reveals sample MBA entry roles, illustrative salary ranges, and a one-line market signal.

Industries covered: Big Tech, Strategy Consulting, Investment Banking, Private Equity/VC, SaaS/Growth Tech, Healthcare/Biotech, CPG/Consumer, Supply Chain/Ops, AI/Data & Analytics, Government/Nonprofit.

**Known limitation:** every score here is editorial (see [provenance](#️-read-this-first-data-provenance)).

### 4. Offer Scorecard

Rate two offers 1–5 on eight weighted dimensions; the tool returns a 0–100 weighted score and a verdict band.

| Dimension | Weight |
|---|---|
| Compensation (TCV) | 25% |
| Growth & promotion velocity | 20% |
| Brand & resume value | 15% |
| Leadership exposure | 15% |
| AI resilience | 10% |
| Work-life fit | 8% |
| Geographic preference | 5% |
| Exit optionality | 7% |

Verdict bands: **80–100** Strong accept · **65–79** Accept with negotiation · **50–64** Proceed with caution · **<50** Decline or renegotiate.

**Note:** the weights are a defensible default, not an empirically validated model. They are editable in code if a coach wants a different philosophy.

### 5. Skill Premium Index

Lists MBA-relevant skills with a 0–100 "premium" score and a category filter (AI & Data, Technical, Business). Intended to prioritize upskilling.

**Known limitation:** scores are editorial estimates of current market demand, not measured salary deltas.

---

## Coach features

- **Session notes** — four fields (student context, offers under review, negotiation levers, next steps). Saved to `sessionStorage`, i.e. **this browser tab/session only**. Notes are **not** synced, not shared, and are lost when the session storage is cleared. Do not treat this as a record-keeping system.
- **Strategic framework quick reference** — condensed talking points.
- **Print / Save PDF** — renders all tabs plus notes for a leave-behind.

---

## Maintenance

Because the data is editorial, it decays. Recommended cadence: **review before each recruiting cycle (at minimum annually).**

All editable values live in clearly labeled JavaScript arrays near the bottom of the HTML file:

- `colData` — city cost-of-living indices and tax rates
- `industries` — the 10 industry objects (scores, roles, ranges, signals)
- `skills` — skill premium scores
- `scoreDims` — scorecard dimensions and weights

Editing requires only a text editor — no build tooling. After editing, open the file in a browser to confirm it renders.

**Privacy note:** the tool runs entirely client-side and transmits nothing. Student inputs never leave the browser. This is a feature (FERPA-friendly) and a constraint (no analytics, no saved records).

---

## Technical notes

- **Single file**, ~1,200 lines, HTML + CSS + vanilla JS. No frameworks.
- External dependencies: Tabler Icons (webfont, CDN) and Google Fonts (EB Garamond, DM Sans). Both optional for core function.
- No cookies, no localStorage of PII, no network calls beyond the two font/icon CDNs.
- Accessibility: semantic headings, ARIA roles on tabs and interactive cells, keyboard-focusable controls. Not formally audited to WCAG.

---

## Versioning

- **v3.0** — Removed MBA ROI tab (low usage, high confusion). Added "How this works" definition banners to every tab. Dropped Chart.js dependency.
- **v2.0** — Added Industry Heatmap; full Eccles branding; coach notes sidebar.
- **v1.0** — Initial five-tool build (TCV, COL, Scorecard, ROI, Skill Index).

---

## License & attribution

Internal tool for the Full-Time MBA Program, David Eccles School of Business, University of Utah. Compensation figures are illustrative estimates for advising use, not financial advice. Students should verify all figures against primary sources before making decisions.

*Maintained by Eccles MBA Career Services.*
