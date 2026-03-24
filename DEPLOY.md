# Deployment Guide — GitHub + Vercel

A step-by-step walkthrough to get your portfolio live.

---

## Part 1 — Push to GitHub

### Prerequisites
- [Git installed](https://git-scm.com/downloads)
- A [GitHub account](https://github.com)
- GitHub CLI (optional but convenient): `winget install GitHub.cli` on Windows

---

### Step 1 — Create a new GitHub repo

1. Go to [github.com/new](https://github.com/new)
2. Name it something clean: `portfolio` or `emmanuelchiefson-portfolio`
3. Set visibility to **Public** (required for Vercel free tier on public projects)
4. **Do NOT** tick "Add README" or "Add .gitignore" — you already have those
5. Click **Create repository**
6. Copy the repo URL shown — it will look like:
   `https://github.com/emmanuelchiefson/portfolio.git`

---

### Step 2 — Initialise git in your project folder

Open a terminal (PowerShell or Command Prompt) and navigate to the `emmanuel-portfolio` folder:

```bash
cd "C:\path\to\emmanuel-portfolio"

git init
git add .
git commit -m "Initial commit — portfolio site"
```

---

### Step 3 — Connect to GitHub and push

```bash
git remote add origin https://github.com/emmanuelchiefson/portfolio.git
git branch -M main
git push -u origin main
```

Your files are now on GitHub. Refresh the repo page to verify.

---

## Part 2 — Deploy to Vercel

### Step 1 — Sign up / log in to Vercel

Go to [vercel.com](https://vercel.com) and click **Sign in with GitHub**. Authorise Vercel to access your GitHub account.

---

### Step 2 — Import your repo

1. From the Vercel dashboard, click **Add New → Project**
2. Find `portfolio` (or whatever you named it) in the list and click **Import**
3. On the configuration screen:
   - **Framework Preset:** Select **Other** (not Next.js or anything else)
   - **Root Directory:** Leave as `.` (the repo root)
   - **Build Command:** Leave blank
   - **Output Directory:** Leave as `.` or leave blank
4. Click **Deploy**

Vercel will deploy in about 30 seconds. You'll get a URL like `https://portfolio-abc123.vercel.app`.

---

### Step 3 — Set a custom Vercel domain (optional but recommended)

1. In your Vercel project settings, go to **Domains**
2. Add a domain like `emmanuelchiefson.vercel.app` (free subdomain) or connect a custom domain if you have one

---

### Step 4 — Add the live URL back into your portfolio

Update your `index.html` meta tags with the live URL:

```html
<meta property="og:url" content="https://your-url.vercel.app">
```

Commit and push — Vercel auto-deploys every push to `main`.

---

## Part 3 — Adding PDFs to /docs/

Every time you complete a BCS or PRINCE2 module:

```bash
# Copy the PDF into the right folder
# e.g. BCS HealthTech case study:
copy "C:\Downloads\medicore-ai.pdf" "C:\path\to\portfolio\docs\medicore-ai.pdf"

# Commit and push
git add docs/medicore-ai.pdf
git commit -m "Add BCS Body of Proof — MediCore AI case study"
git push
```

Vercel deploys in ~30 seconds. The PDF is then live at:
`https://your-url.vercel.app/docs/medicore-ai.pdf`

The `vercel.json` config already tells Vercel to serve PDFs inline (opens in the browser viewer rather than forcing a download). This means the embedded viewer in your portfolio page will work correctly.

---

## Part 4 — Expected file paths (must match index.html)

Your portfolio page already references these paths — match them exactly:

| Document | Path |
|---|---|
| BCS BA — MediCore AI | `/docs/medicore-ai.pdf` |
| BCS BA — NovaPay | `/docs/novapay.pdf` |
| BCS BA — Meridian Consulting | `/docs/meridian-consulting.pdf` |
| PRINCE2 Agile coursework | `/docs/prince2-agile/module-name.pdf` |
| CV / Resume | `/assets/emmanuel-chiefson-cv.pdf` |

---

## Quick reference commands (day-to-day)

```bash
# Pull latest (if editing from multiple machines)
git pull

# Add a new PDF
git add docs/novapay.pdf
git commit -m "Add BCS BA — NovaPay case study"
git push

# Add any updated file
git add index.html
git commit -m "Update credentials section"
git push
```

---

## Troubleshooting

| Issue | Fix |
|---|---|
| PDF forces download instead of opening inline | Check `vercel.json` is in the repo root and was committed |
| Vercel deployment fails | Check the Vercel dashboard logs — usually a JSON syntax error in `vercel.json` |
| Changes pushed but site not updated | Check the Vercel dashboard — deployments tab — for the status |
| CORS error on fonts | Fonts load from Google CDN — should work on Vercel with no changes |
