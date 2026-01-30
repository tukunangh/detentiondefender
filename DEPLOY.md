# DetentionDefender — Deployment Guide

## Files Ready
- `index.html` — Full landing page (static HTML, no build needed)
- `worker.js` — Cloudflare Worker version (for CF deployment)
- `wrangler.toml` — Worker config

## Formspree Setup (Required)

1. Login to https://formspree.io (creds in TOOLS.md)
2. Create new form → Name: "DetentionDefender Early Access"
3. Copy the form ID (looks like `xwpoppbe`)
4. Replace `xwpoppbe` in index.html with the real form ID (2 places)

## Deployment Options

### Option A: Cloudflare Pages (Manual)
1. Go to https://dash.cloudflare.com → Pages
2. Create project → Upload files
3. Upload `index.html`
4. Done: `detentiondefender.pages.dev`

### Option B: Cloudflare Worker
Requires API token with Workers permissions:
```bash
cd /root/clawd/projects/detentiondefender
CLOUDFLARE_API_TOKEN="<token>" npx wrangler deploy
```
Result: `detentiondefender.<account>.workers.dev`

### Option C: Vercel
```bash
npm i -g vercel
cd /root/clawd/projects/detentiondefender
vercel --prod
```

### Option D: Render.com
1. Connect GitHub repo
2. Static site → point to this folder
3. Auto-deploys on push

## Custom Domain (Optional)
After smoke test validation, can add:
- `detentiondefender.com`
- Or subdomain under existing domain

## Analytics (Recommended)
Add before `</head>`:
```html
<script defer src="https://plausible.io/js/script.js" data-domain="detentiondefender.pages.dev"></script>
```

Or use free Cloudflare Web Analytics.

## Post-Deployment Checklist
- [ ] Test email capture form
- [ ] Check mobile responsiveness  
- [ ] Set up Plausible/CF Analytics
- [ ] Create $50 ad budget plan
- [ ] Identify first distribution channels
