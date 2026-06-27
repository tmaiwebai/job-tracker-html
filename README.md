# Job Application Tracker

AI-powered job application tracker with fit scoring, resume generation, and Airtable persistence.

## Features
- Paste a job description → Claude scores fit against your resume
- Fit score, matched skills, gaps, ATS keywords, resume tweaks, talking points
- Generate tailored resume (.docx) — 5 templates auto-detected from JD
- 👍 / 👎 feedback loop for training data
- Logs every application to Airtable

---

## Stack
- GitHub Pages (hosting)
- Cloudflare Worker (Claude API proxy)
- Airtable (persistence)
- pdf.js (resume parsing)
- JSZip (docx generation)

---

## Setup Instructions

### 1. Airtable
1. Go to airtable.com → create a free account
2. Create a new base named `Job Applications`
3. Create a table named `Applications` with these columns:
   - `Date` — Single line text
   - `Company` — Single line text
   - `Role` — Single line text
   - `Score` — Number
   - `Apply` — Single line text
   - `Verdict` — Single line text
   - `Matched Skills` — Single line text
   - `Gaps` — Single line text
   - `ATS Keywords` — Single line text
   - `Resume Generated` — Single line text
   - `Feedback` — Single line text
   - `Feedback Note` — Long text
   - `Raw Prompt` — Long text
   - `Raw Completion` — Long text
4. Go to airtable.com/create/tokens → create a Personal Access Token
   - Scopes: `data.records:read` and `data.records:write`
   - Access: select your `Job Applications` base
   - Copy the token — you only see it once
5. Copy your Base ID from the URL: `airtable.com/appXXXXXXXXXX/...`

### 2. Anthropic API Key
1. Go to console.anthropic.com
2. Create an API key
3. Copy it — needed for Cloudflare Worker

### 3. Cloudflare Worker (Claude API Proxy)
1. Go to cloudflare.com → create a free account
2. Go to Compute → Create Worker → Start with Hello World
3. Name it `claude-proxy`
4. After deploying, click the `</>` tab to open the editor
5. Replace all code with the contents of `claude-proxy-worker.js`
6. Click Deploy
7. Go to Settings → Variables and Secrets → Add Secret:
   - Name: `ANTHROPIC_API_KEY`
   - Value: your Anthropic API key
8. Copy your worker URL: `https://claude-proxy.yoursubdomain.workers.dev`

### 4. GitHub Pages
1. Go to github.com → create a new repository named `job-tracker-html` (Public)
2. Upload `JobTracker_Phase2.html`
3. Go to Settings → Pages → Deploy from branch → main → / (root) → Save
4. Wait 60 seconds → live at `https://yourusername.github.io/job-tracker-html/JobTracker_Phase2.html`

### 5. Tracker Settings
1. Open your live GitHub Pages URL
2. Click Settings tab
3. Enter your Airtable Base ID and API Token → Save → Test connection
4. Upload your resume PDF using the pill in the header

---

## Files
- `JobTracker_Phase2.html` — main application
- `claude-proxy-worker.js` — Cloudflare Worker proxy code
- `JobTracker_AppScript.gs` — Google Apps Script (deprecated, replaced by Airtable)

---

## Cost Estimates
- Scoring: ~$0.02–0.04 per analysis
- Resume generation: ~$0.05–0.08 per resume
- Hosting: free (GitHub Pages + Cloudflare free tier + Airtable free tier)
