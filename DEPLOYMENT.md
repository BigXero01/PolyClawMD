# Deployment Guide

## Push to GitHub

### 1. Create a GitHub Repository

```bash
# Go to https://github.com/new
# Create a new repository named "trading-analysis-agent"
# Do NOT initialize with README (we already have one)
```

### 2. Push Your Code

```bash
cd /home/ubuntu/.openclaw/workspace/trading-agent

# Add your GitHub remote (replace YOUR_USERNAME)
git remote add origin https://github.com/YOUR_USERNAME/trading-analysis-agent.git

# Push to GitHub
git branch -M main
git push -u origin main
```

## Deploy to Netlify

### Option 1: Connect GitHub (Recommended - Auto-Deploy)

1. Go to [netlify.com](https://netlify.com)
2. Click **"New site from Git"**
3. Select **GitHub**
4. Authorize Netlify to access your GitHub account
5. Select the `trading-analysis-agent` repository
6. Settings:
   - **Branch to deploy**: `main`
   - **Build command**: Leave empty (static site)
   - **Publish directory**: `.` (or leave empty)
7. Click **"Deploy site"**

**Result**: Your site is live! Netlify auto-deploys when you push to GitHub.

### Option 2: Drag & Drop (One-Time)

1. Go to [netlify.com/drop](https://netlify.com/drop)
2. Drag the entire `trading-agent` folder onto the page
3. Wait for deployment to complete
4. Your site is live at a random Netlify URL

**Note**: This is one-time only. For auto-deploy, use Option 1.

### Option 3: Netlify CLI

```bash
npm install -g netlify-cli

cd /home/ubuntu/.openclaw/workspace/trading-agent

# Login to Netlify (opens browser)
netlify login

# Deploy
netlify deploy --prod
```

## Custom Domain (Optional)

Once deployed to Netlify:

1. Go to your site settings → **Domain management**
2. Click **"Add custom domain"**
3. Enter your domain (e.g., `trading-agent.com`)
4. Follow DNS setup instructions

## Environment Variables (Optional)

For API key via environment variable instead of manual entry:

1. In Netlify dashboard: **Site settings** → **Build & deploy** → **Environment**
2. Add: `ANTHROPIC_API_KEY` = your API key
3. Modify `index.html` line 294:

```javascript
const apiKey = window.ENV?.ANTHROPIC_API_KEY || 
               document.getElementById('apiKey').value;
```

## Verify Deployment

1. Visit your Netlify URL
2. Enter test market data
3. Click "Analyze Markets"
4. Should see Claude's analysis within seconds

## Update Your Site

### After Making Changes Locally

```bash
cd /home/ubuntu/.openclaw/workspace/trading-agent

# Make your changes...
git add .
git commit -m "Your commit message"
git push origin main
```

Netlify automatically redeploys! Check deployment status in the Netlify dashboard.

## Performance Tips

- Site is **lightning fast** (pure static HTML/CSS/JS)
- No server needed — runs 100% in visitor's browser
- API calls go directly to Anthropic, bypassing your server
- Scales infinitely with Netlify's CDN

## Troubleshooting

### "Deploy shows failed"
- Check Netlify logs (in dashboard)
- Usually just a syntax error in HTML/CSS
- Fix locally, commit, push again

### "Site not updating"
- Netlify may cache for 5-10 minutes
- Hard refresh your browser (Ctrl+Shift+R)
- Clear browser cache

### "API requests failing"
- Check your Anthropic API key is valid
- Check your account has quota remaining
- Look at browser DevTools → Network tab

## Next Steps

- Add more market feeds (pull live price data from APIs)
- Integrate WebSocket for real-time updates
- Add historical analysis charts
- Store analysis history in IndexedDB
- Add alert system for trade signals