# WoW Leaderboard Project

Automated data processing and leaderboard system for World of Warcraft mythic+ data.

## 🚀 What This Does

This project provides automated data processing for World of Warcraft leaderboards through:

1. **Backend API** (`wow-api/`) - Node.js server with PostgreSQL database
2. **Frontend Dashboard** (`wow-leaderboard-frontend/`) - React application for data visualization
3. **Automation Jobs** - Scripts for automated data fetching and processing
4. **GitHub Actions** (`wow-automation/`) - Automated workflows for data processing

## 📊 Automation Jobs

### Current Period Job (`job-daily-current-period.js`)
Fetches and processes data for the **latest period** of the current season.

**Features:**
- Automatically detects the latest season and period
- Fetches mythic leaderboard data for all regions (US, EU, KR, TW)
- Imports data into the database
- Performs cleanup and optimization tasks
- Refreshes materialized views

**Usage:**
```bash
cd wow-api/scripts
node job-daily-current-period.js
```

### Previous Period Job (`job-daily-previous-period.js`)
Fetches and processes data for the **previous period** with intelligent period selection.

**Logic:**
- **If current season has multiple periods**: Fetches the second-to-last period
- **If current season has only 1 period**: Fetches the last period from the previous season

**Features:**
- Smart period selection based on season structure
- Same data processing pipeline as current period job
- Useful for historical data analysis
- Handles edge cases when seasons have limited periods

**Usage:**
```bash
cd wow-api/scripts
node job-daily-previous-period.js
```

## ⏰ GitHub Actions Schedule

- **Weekly automation** - Runs automatically via GitHub Actions
- **Manual trigger** - Available anytime through GitHub Actions UI
- **Render One-Off Jobs** - Executed on Render platform

## 🔧 Setup

### 1. Repository Structure
```
wow-project/
├── wow-api/                    # Backend API server
│   ├── scripts/               # Automation scripts
│   │   ├── job-daily-current-period.js
│   │   └── job-daily-previous-period.js
│   └── src/                   # API source code
├── wow-leaderboard-frontend/   # React frontend
├── wow-automation/            # GitHub Actions workflows
└── README.md                  # This file
```

### 2. Environment Variables

**Backend (wow-api/):**
- `API_BASE_URL` - Base URL for API requests
- `RENDER_API_KEY` - Render API key for automation
- Database connection variables

**Frontend (wow-leaderboard-frontend/):**
- `VITE_API_BASE_URL` - Backend API URL

### 3. GitHub Actions Setup

The `wow-automation/` repository contains:
- **Weekly automation workflow** - Triggers Render One-Off Jobs
- **Manual trigger capability** - For testing and on-demand runs
- **Error handling and logging** - Comprehensive monitoring

## 📈 Data Processing Pipeline

1. **Fetch** - Retrieve leaderboard data from Blizzard API for all regions
2. **Import** - Process and store data in PostgreSQL database
3. **Cleanup** - Remove old/duplicate data to maintain performance
4. **Optimize** - Perform VACUUM FULL on database
5. **Refresh** - Update materialized views for fast analytics queries

## 🛠️ Technologies

- **Node.js** - Backend API and automation scripts
- **React** - Frontend dashboard
- **PostgreSQL** - Data storage and processing
- **GitHub Actions** - Automation platform
- **Render** - Backend hosting and One-Off Jobs
- **Vercel** - Frontend hosting

## 📊 Monitoring

- **GitHub Actions** - View workflow runs and logs
- **Render Dashboard** - Monitor One-Off Job execution
- **Manual trigger** - Test automation anytime via GitHub Actions UI
- **Email notifications** - Get notified of success/failure

## 🚀 Deployment

### Backend (Render)
- API server deployed on Render
- Uses PostgreSQL database
- Automated deployments via GitHub Actions

### Frontend (Vercel)
- React application deployed on Vercel
- Automatic deployments on push to main branch

## 🔄 Development

### Running Locally
```bash
# Backend
cd wow-api
npm install
npm start

# Frontend
cd wow-leaderboard-frontend
npm install
npm run dev
```

### Testing Automation Jobs
```bash
# Test current period job
cd wow-api/scripts
node job-daily-current-period.js

# Test previous period job
cd wow-api/scripts
node job-daily-previous-period.js
```

## 📝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test automation jobs locally
5. Submit a pull request

## 📄 License

[Add your license information here] 