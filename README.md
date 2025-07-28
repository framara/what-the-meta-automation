# WoW Automation

Automated daily data fetching and processing for World of Warcraft leaderboard application.

## 🚀 What This Does

This repository contains GitHub Actions workflows that automatically trigger your Render One-Off Jobs to:

1. **Fetch leaderboard data** from all 4 regions (US, EU, KR, TW)
2. **Import and process** the collected data
3. **Clean up old data** to maintain performance
4. **Perform database optimization** (VACUUM FULL)
5. **Refresh materialized views** for analytics

## ⏰ Schedule

- **Daily at 1:00 AM UTC** (automated)
- **Manual trigger** available anytime

## 🔧 Setup

### 1. Create GitHub Repository
- Repository name: `wow-automation`
- Make it **Public** (for free GitHub Actions)

### 2. Add Secrets
Go to **Settings** → **Secrets and variables** → **Actions** and add:
- **Name:** `RENDER_API_KEY`
- **Value:** Your Render API key

### 3. Push This Code
```bash
git add .
git commit -m "Add GitHub Actions automation"
git push origin main
```

## 📊 Monitoring

- **Actions tab** - View workflow runs and logs
- **Manual trigger** - Click "Run workflow" to test
- **Email notifications** - Get notified of success/failure

## 🛠️ Technologies

- **GitHub Actions** - Automation platform
- **Render One-Off Jobs** - Serverless execution
- **Node.js** - Automation scripts
- **PostgreSQL** - Data storage and processing 