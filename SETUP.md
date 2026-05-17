# Team Dashboard Setup

## Overview
The team dashboard is a separate web app that aggregates stats from all builders' CRMs.

## Architecture
1. **Central Dashboard** - Lives at `https://michael9549.github.io/team-dashboard/`
2. **Individual CRMs** - Each builder has their own CRM that syncs stats to the dashboard
3. **Data Storage** - Stats stored in `michael9549/team-dashboard-data` repo

## Setup Steps

### 1. Create the Dashboard Repo
Go to GitHub and create a new repository:
- Name: `team-dashboard`
- Private: No (needs to be public for GitHub Pages)
- Initialize with README: Yes

### 2. Create the Data Repo
Create another repository:
- Name: `team-dashboard-data`
- Private: Yes (contains builder data)
- Initialize with README: Yes

### 3. Deploy the Dashboard
Upload `index.html` to the `team-dashboard` repo and enable GitHub Pages.

### 4. Configure Each Builder's CRM
In each builder's CRM (`index.html`), update the `TEAM_DASHBOARD_CONFIG`:

```javascript
const TEAM_DASHBOARD_CONFIG = {
  enabled: true,
  builderName: 'John Smith',  // Builder's name as shown on dashboard
  dashboardRepo: 'michael9549/team-dashboard-data',
  dashboardToken: 'ghp_...'  // GitHub token with access to dashboard-data repo
};
```

## How It Works
1. Builder saves a lead in their CRM
2. CRM automatically syncs stats (not lead details) to central dashboard
3. Dashboard aggregates all builder stats and displays them
4. Stats update in real-time on every save

## Privacy
- Only stats are synced (counts, not names/emails)
- Individual lead data stays in each builder's private repo
- Dashboard shows aggregated team data only
