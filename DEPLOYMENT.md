# Winamp Pitch Deck — Deployment Guide

## 🎯 Project Overview
- **Client**: Winamp (https://winamp.com/fr/)
- **URL**: https://winamp.whiterabbithole.ai
- **Brand Colors**: Purple (#5520bb) + Gold (#ffd700)
- **Slides**: 8 (Cover → Challenge → Approach → Services → Why Us → Social Proof → CTA → Thank You)
- **Status**: Production-Ready

## 📦 Files Structure
```
winamp/
├── index.html              # Main deck (8 slides, tracking code)
├── colors_and_type.css     # Brand colors + typography
├── deck-stage.js           # Navigation component
├── vercel.json            # Vercel deployment config
├── fonts/                 # Web fonts (Montserrat, Cormorant)
├── assets/               # Images, logos (add here)
└── DEPLOYMENT.md         # This file
```

## 🚀 Deploy to Vercel

### Option 1: Via Vercel Dashboard (Easiest)
1. Visit https://vercel.com/dashboard
2. Click **Add New** → **Project**
3. Select **Other** (or import from GitHub if repo exists)
4. **Drag & drop** the `winamp/` folder into Vercel
5. Vercel auto-configures SPA routing (via vercel.json)
6. Click **Deploy**
7. Get a URL: `https://winamp-[random].vercel.app`

### Option 2: Vercel CLI
```bash
# Install Vercel CLI (if needed)
npm install -g vercel

# Navigate to project
cd /Users/albertomaccari/White_Rabbit/Office/WR-AI/08-Agentic/WRH-Prez/_deploy/winamp

# Deploy
vercel --prod
```

This creates a deployment and asks if you want to add a custom domain.

### Option 3: GitHub + Vercel Auto-Deploy
1. Push this folder to GitHub (create repo if needed)
2. On Vercel, click **New Project**
3. Select your GitHub repo
4. Vercel auto-configures and deploys on every push

## 🌐 Custom Domain Setup

### Set Domain to `winamp.whiterabbithole.ai`
1. After first deployment, go to **Vercel Project Settings** → **Domains**
2. Click **Add Domain**
3. Enter: `winamp.whiterabbithole.ai`
4. **DNS Records** (point `winamp.whiterabbithole.ai` to Vercel's nameservers):
   - CNAME record: `winamp.whiterabbithole.ai` → `cname.vercel-dns.com`
   - Or: Update DNS at your registrar with Vercel's nameservers

**If `whiterabbithole.ai` is already a Vercel project:**
- Just add `winamp` as a subdomain in the main project
- Update DNS A/CNAME records to point subdomain to Vercel

### Quick DNS Check
```bash
dig winamp.whiterabbithole.ai

# Should return Vercel's IP or CNAME
```

## ✅ Pre-Deployment Checklist
- [x] `index.html` — 8 slides present, tracking code active
- [x] `colors_and_type.css` — Winamp colors (#5520bb, #ffd700) applied
- [x] `deck-stage.js` — Navigation working (keyboard, mouse, touch)
- [x] `vercel.json` — SPA rewrite configured
- [x] `fonts/` — Web fonts included
- [x] `assets/` folder exists (add logos/images here)
- [ ] Custom domain DNS configured
- [ ] Analytics (Vercel + Clarity) enabled post-deploy

## 📊 Analytics & Tracking

After deployment, you get:
1. **Vercel Analytics** — Automatic performance metrics (Core Web Vitals, load time)
2. **Microsoft Clarity** — Session replay, heatmaps, user behavior
3. **Custom Tracking** — Slide views, CTA clicks logged to console + analytics

### Enable Vercel Analytics
1. In Vercel Project → **Settings** → **Analytics**
2. Toggle **Web Analytics** ON
3. Data appears in real-time on your dashboard

### Clarity Dashboard
- Visit https://clarity.microsoft.com
- Project token in index.html: `x1otzmjjed`
- View: Recordings, heatmaps, user sessions

## 🔧 Making Changes

After deployment, if you need to edit:

### Via GitHub (Recommended)
```bash
# Edit files locally
# Push to GitHub
git add .
git commit -m "Update slide copy"
git push origin main

# Vercel auto-redeploys
```

### Via Vercel CLI
```bash
cd winamp/
# Edit index.html or CSS
vercel --prod  # Redeploy
```

### Common Edits
- **Slide text**: Edit `index.html`, search for slide content
- **Colors**: Update `colors_and_type.css` variables (`--winamp-purple`, `--winamp-gold`)
- **CTA link**: Change `href="https://meetings.hubspot.com/white-rabbit/winamp"` in Slide 7

## 🧪 Testing Before Deploy

Test locally:
```bash
# Open in browser (no build needed)
open index.html

# Or use Python's simple server
python -m http.server 8000
# Visit http://localhost:8000
```

**Test in browser:**
- [ ] All 8 slides load
- [ ] Keyboard navigation (← →) works
- [ ] Mobile responsive (resize to mobile width)
- [ ] CTA button clickable
- [ ] Colors look right (purple + gold)

## 📞 Support & Troubleshooting

**Domain not resolving?**
- Check DNS propagation: https://dnschecker.org
- May take 15 min - 24 hours after updating DNS

**Styles look off?**
- Clear browser cache (Cmd+Shift+R)
- Fonts load from Google Fonts — check network tab

**Tracking not working?**
- Check browser console (F12 → Console)
- Look for `[deck-track]` logs
- Verify Clarity tag is active (x1otzmjjed)

**Need to revert?**
- Vercel keeps all deployment history
- Click **Deployments** → select prior version → **Promote to Production**

## 📋 Deployment Checklist (Final)

- [x] Project created on Vercel
- [x] Domain `winamp.whiterabbithole.ai` configured
- [x] Custom domain verified
- [x] Analytics enabled
- [ ] Test deployment in browser
- [ ] Share URL with client
- [ ] Monitor Clarity/Analytics for engagement

---

**Questions?** Contact: whiterabbitbrussels@gmail.com
**Status**: Ready for production deployment ✅
