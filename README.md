# Emmanuel Chiefson — Portfolio

Personal portfolio site for Emmanuel Chiefson — Technical Project & Platform Transformation Lead.

**Live site:** [your-project-name.vercel.app](https://your-project-name.vercel.app)

---

## Tech Stack

Plain HTML/CSS/JS — no build step required. Deployed as a static site via Vercel.

---

## Repo Structure

```
portfolio/
├── index.html              # Main portfolio page
├── vercel.json             # Vercel deployment config (PDF headers, security headers)
├── .gitignore
├── docs/                   # Evidence portfolio — served as inline PDFs
│   ├── medicore-ai.pdf         # BCS BA — HealthTech case study
│   ├── novapay.pdf             # BCS BA — FinTech case study
│   ├── meridian-consulting.pdf # BCS BA — Professional Services case study
│   └── prince2-agile/          # PRINCE2 Agile coursework PDFs
│       └── (module files here)
└── assets/                 # Images, CV PDF, and other static assets
```

---

## Adding a PDF

1. Save the PDF to the correct folder:
   - BCS Body of Proof → `docs/medicore-ai.pdf`, `docs/novapay.pdf`, `docs/meridian-consulting.pdf`
   - PRINCE2 Agile coursework → `docs/prince2-agile/module-1.pdf` (or similar)
2. Commit and push — Vercel deploys automatically within ~30 seconds.
3. The PDF will appear inline in the portfolio viewer at `/docs/filename.pdf`.

---

## Local Development

No build step needed. Just open `index.html` in a browser, or use a simple local server:

```bash
# Python 3
python3 -m http.server 8000

# Then visit http://localhost:8000
```

---

## Deployment

Hosted on [Vercel](https://vercel.com). Every push to `main` triggers an automatic deployment.

---

## Contact

Emmanuel Chiefson · [emmanuelchiefson@gmail.com](mailto:emmanuelchiefson@gmail.com) · [LinkedIn](https://www.linkedin.com/in/emmanuelchiefson/)
