# iFeed Market Research · public site

Static HTML site · no build step · deploys directly to Netlify.

**Target URL:** https://ifeedmarketresearch.netlify.app/

---

## What's inside

```
iFeed_Market_Research/
├── index.html                  ← Home
├── about.html                  ← About
├── industries.html             ← Industries we cover
├── services.html               ← What we offer
├── methodology.html            ← How we research
├── consulting.html             ← Consulting services
├── custom-research.html        ← Custom research
├── training.html               ← Training programs
├── proven-record.html          ← Track record
├── horizon.html                ← What's coming
├── faq.html                    ← FAQ
├── request-sample.html         ← Request sample form
├── customize.html              ← Customize a report
├── how-to-order.html           ← Ordering guide
├── speak-to-analyst.html       ← Book analyst call
├── contact.html                ← Contact
├── privacy.html                ← Privacy policy
├── terms.html                  ← Terms
├── sitemap.html                ← Sitemap
├── 404.html                    ← 404 fallback
│
├── samples/                    ← Free sample pages (per domain)
│   ├── bioanalytical.html
│   ├── bioequivalence.html
│   ├── clinical-trials.html
│   ├── medical-devices.html
│   ├── governance-qms.html
│   └── lims.html
│
├── reports/                    ← Full reports (paid · 6 domains)
│   ├── bioanalytical-full.html
│   ├── bioequivalence-full.html
│   ├── clinical-trials-full.html
│   ├── medical-devices-full.html
│   ├── governance-qms-full.html
│   ├── lims-full.html
│   ├── MRA-REP-001_Bioanalytical.html       ← original MRA-REP series
│   ├── MRA-REP-002_Bioequivalence.html
│   ├── MRA-REP-003_Clinical_Trials.html
│   ├── MRA-REP-004_Medical_Devices.html
│   ├── MRA-REP-005_Quality_Governance.html
│   └── MRA-REP-006_LIMS.html
│
├── platform.css                ← shared CSS (legacy · most pages have inline)
├── netlify.toml                ← Netlify build + redirect config
├── _redirects                  ← Netlify redirect rules
├── robots.txt                  ← SEO directives
└── .gitignore
```

**Total:** 25 nav pages + 6 sample pages + 12 report pages = **43 HTML files**.

---

## Brand

iFeed Market Research uses sage + gold + bone palette · Source Serif 4 + Inter + JetBrains Mono fonts. Same as the embedded reports in the unified cockpit Market Research canvas.

| Token | Light value |
|---|---|
| `--bone` | `#FAFAF7` (page background) |
| `--white` | `#FFF` (surface) |
| `--ink` | `#0D0D0E` (heading text) |
| `--ink-soft` | `#3A3A3D` (body text) |
| `--mute` | `#8E8E93` (meta) |
| `--hair` | `#E5E5EA` (rule lines) |
| `--sage` / `--sage-deep` | `#7A9B86` / `#4A6B56` (primary accent · links · CTAs) |
| `--gold` / `--gold-deep` | `#B89868` / `#8E6F42` (secondary accent · eyebrows) |
| `--signal` | `#C4432B` (warning / verify) |

---

## Local preview

```bash
cd ~/OER/03_CONTENT/iFeed_Market_Research
python3 -m http.server 8080
# open http://localhost:8080
```

---

## Deploy to Netlify

See `DEPLOYMENT_RUNBOOK.md` for the full step-by-step (GitHub → Netlify).

Quick version:

1. Push this folder to a new GitHub repo (e.g., `iFeedMarketResearch`)
2. Connect the repo to Netlify
3. Build settings:
   - Build command: *(leave empty)*
   - Publish directory: `.`
4. Set site name to `ifeedmarketresearch` so the URL becomes `ifeedmarketresearch.netlify.app`
5. Deploy.

---

## Pricing model (placeholder · update before final publish)

The site currently shows "Indicative pricing · contact for current" — this is intentional. Real prices must be set in:
- `samples/*.html` right-rail buy box (look for `INDICATIVE_PRICING`)
- `reports/*-full.html` right-rail buy box

Recommend two paid tiers:
- **Single-User License** · suggested €1,500-2,500
- **Corporate License** · suggested €4,000-6,000 (or "From €X · contact for quote")

Plus a free sample request form (already wired to `mailto:upbringing.eipfm@outlook.com`).

---

## Contact

- Email: `upbringing.eipfm@outlook.com` (registered iFeed.ie contact)
- Domain (if/when ready): `ifeedmarketresearch.com` or similar — currently Netlify subdomain

---

## Notes

- All sample pages were synthesized from the L3 comprehensive reports using `cockpit_report.parse_author_html` + `market_report_layout.render_sample_page`. They show the buyer the FULL TOC + tables included + deliverables + sample excerpt + methodology + why-buy panel + indicative pricing.
- All full report pages were rendered using `market_report_layout.render_market_report` from the L2 production HTML.
- The MRA-REP-001-006 reports in `reports/` are the original author HTML (kept for reference).
- See `~/Agent_Workflow_Vault/05_CONTROL_TOWER/unified_cockpit/lib/market_report_layout.py` for the rendering pipeline.

---

*Site bootstrapped 2026-05-20 · iFeed Market Research v1*
