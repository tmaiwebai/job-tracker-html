# Job Application Tracker

AI-powered job application tracker with fit scoring, resume generation, and Airtable persistence.

## Features
- Paste a job description → Claude scores fit against your resume
- Fit score, matched skills, gaps, ATS keywords, resume tweaks, talking points
- Generate tailored resume (.docx) — 5 templates auto-detected from JD
- 👍 / 👎 feedback loop for training data
- Logs every application to Airtable

## Stack
- GitHub Pages (hosting)
- Cloudflare Worker (Claude API proxy)
- Airtable (persistence)
- pdf.js (resume parsing)
- JSZip (docx generation)
