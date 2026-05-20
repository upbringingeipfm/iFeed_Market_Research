# Deployment Runbook · iFeed Market Research → Netlify

**Target URL:** `https://ifeedmarketresearch.netlify.app/`

This site is static HTML · no build step · deploys in minutes.

You'll do 3 things in sequence:
1. **Push to GitHub** (one-time setup)
2. **Connect Netlify to the GitHub repo** (one-time setup)
3. **Set the Netlify site name** so the URL ends in `ifeedmarketresearch.netlify.app`

After this, every `git push` auto-deploys.

---

## Why this can't be fully automated for you

- Creating GitHub repos requires your GitHub login
- Connecting Netlify needs you to authorize Netlify to read the repo
- Claiming the `ifeedmarketresearch.netlify.app` subdomain has to be done from your Netlify account

Everything else is ready to push.

---

## Step 1 · Push to GitHub

### 1a · Confirm git repo is initialized (already done by setup script)

```bash
cd ~/OER/03_CONTENT/iFeed_Market_Research
git status
# should show: "On branch main · nothing to commit, working tree clean"
```

### 1b · Create a new repo on GitHub

Open in browser: https://github.com/new

Settings:
- **Repository name:** `iFeedMarketResearch`
- **Description:** `iFeed Market Research · public site · regulator-grade market intelligence`
- **Public** (so Netlify free tier can deploy without paid plan)
- **Do NOT** initialize with README, .gitignore, or license (we already have these)

Click **Create repository**.

### 1c · Connect this local repo to the new GitHub repo

GitHub will show you commands · paste these into your terminal (replace `YOUR-USERNAME`):

```bash
cd ~/OER/03_CONTENT/iFeed_Market_Research
git remote add origin https://github.com/YOUR-USERNAME/iFeedMarketResearch.git
git branch -M main
git push -u origin main
```

If you're using SSH instead of HTTPS:
```bash
git remote add origin git@github.com:YOUR-USERNAME/iFeedMarketResearch.git
```

If you get an auth prompt:
- HTTPS: use a Personal Access Token (Settings → Developer settings → Personal access tokens → Generate new · classic · with `repo` scope)
- SSH: make sure your SSH key is added to GitHub (Settings → SSH and GPG keys)

---

## Step 2 · Connect Netlify

### 2a · Open Netlify

Open in browser: https://app.netlify.com/

Sign in if you're not already (recommend "Sign in with GitHub" so authorization is automatic).

### 2b · Add a new site

Click **Add new site** → **Import an existing project**

### 2c · Connect GitHub

Click **Deploy with GitHub**.

If Netlify asks for repo access, grant it (you can scope to just this one repo or all repos · either works).

### 2d · Pick the repo

Find and click `iFeedMarketResearch` from the list.

### 2e · Configure build settings

Netlify will show a build settings page. Override:
- **Branch to deploy:** `main`
- **Build command:** *(leave EMPTY)*
- **Publish directory:** `.` (just a dot)
- **Functions directory:** *(leave default)*

Click **Deploy site**.

Netlify will start the first build and assign a random URL like `https://magnificent-pony-abc123.netlify.app/`. We'll rename this in step 3.

### 2f · Wait for deploy

The build usually completes in 30-90 seconds. Watch the deploy log.

When it shows **Published**, the site is live at that random URL.

---

## Step 3 · Rename to ifeedmarketresearch.netlify.app

### 3a · Open Site Settings

In Netlify dashboard → click your new site → **Site configuration** (left sidebar).

### 3b · Change site name

Click **Change site name**.

Type: `ifeedmarketresearch`

Click **Save**.

The URL is now `https://ifeedmarketresearch.netlify.app/`.

(If that name is already taken — Netlify will say so — try `ifeed-market-research` or `ifeedmr` or whatever variant is free.)

---

## Step 4 · Test the live site

Open the URL in a browser. Walk through:
- [ ] Home page loads
- [ ] Top nav clicks work (About · Industries · Services · Methodology · Consulting)
- [ ] Click a domain sample (e.g., `/sample/bioanalytical`)
- [ ] Sample page shows: deliverables grid · full TOC · tables list · excerpt · methodology · why-buy · pricing rail
- [ ] Click a full report (e.g., `/report/bioanalytical`)
- [ ] Full report shows: hero · 3-col grid · TOC left · content center · buy rail right · footer
- [ ] 404 page works (try `/this-does-not-exist`)
- [ ] CTA mailto links open your mail client with subject pre-filled

---

## Step 5 · Future updates

Once everything's connected:

```bash
cd ~/OER/03_CONTENT/iFeed_Market_Research
# edit files
git add .
git commit -m "Update: <what changed>"
git push
```

Netlify auto-deploys within a minute.

---

## Troubleshooting

**"Site name already taken" when renaming**
→ Try `ifeed-market-research` or `ifeedmr`. Netlify subdomains are first-come-first-served.

**Pages 404 in browser but files exist**
→ Check `_redirects` and `netlify.toml` are at the repo root (not in a subfolder). Re-deploy.

**Fonts not loading**
→ Check `https://fonts.googleapis.com` is reachable. If Netlify blocks external requests, the CSS still inlines `Georgia` and `system-ui` fallbacks, so it degrades gracefully.

**Wants a custom domain (not netlify.app)**
→ In Site settings → Domain management → Add custom domain. Buy domain from GoDaddy/Namecheap/etc. Add Netlify DNS or CNAME. Wait for propagation.

---

## What's the actual content on the site

| Page count | Type |
|---|---|
| 19 | Nav pages (home · about · industries · services · methodology · consulting · custom research · training · proven record · horizon · FAQ · request sample · customize · how to order · speak to analyst · contact · privacy · terms · sitemap) |
| 6 | Synthesized sample pages (one per domain · `/samples/`) |
| 6 | Full report pages with iFeed MR chrome (`/reports/`) |
| 12 | Original MRA-REP HTML reports + TOC + segmentation (`/reports/`) |
| 1 | 404 page |
| **44** | **Total HTML files** |

Plus: `netlify.toml` · `_redirects` · `robots.txt` · `.gitignore` · `README.md` · `DEPLOYMENT_RUNBOOK.md` (this file) · `platform.css`.

---

## Contact

If anything fails during deployment, the issue is most likely:
1. GitHub auth (need PAT or SSH key)
2. Netlify auth (need to grant repo access)
3. Site name taken (try a variant)

All three are 60-second fixes from the Netlify UI.

---

*Runbook · 2026-05-20 · iFeed Market Research v1*
