# System Health Monitor

This project collects system health data from multiple machines and displays it in a centralized dashboard.

## Folder Structure - refererense purpose

```
system-health-monitor/
│
├── utility/                # Python/Node.js utility (runs on machines)
│   ├── main.py             # Entry point
│   ├── checks.py           # System check functions (Python only)
│   ├── utils.py            # Helper functions (Python only)
│   ├── config.json         # Configuration for API URL, intervals
│   └── requirements.txt    # Python dependencies
│
├── backend/                # Express + MongoDB API
│   ├── models
│   ├── routes/report.js
    ├── controllers
│   ├── server.js
│   └── package.json
│
├── frontend/               # React + Vite Dashboard
│   ├── src/
│   │   ├── components/
│   │   │   └── Dashboard.jsx
│   │   └── App.jsx
│   └── package.json
│
└── README.md               # Documentation
```

---

## Setup Instructions

### Backend (Node.js + MongoDB)

1. **Clone the repo:**

   ```bash
   git clone https://github.com/praneethrms04/system-health-monitor.git
   cd system-health-monitor/backend
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Environment variables (`.env`):**

   ```bash
   PORT=5000
   MONGODB_URI=<your_mongo_uri>
   AGENT_API_KEYS=dev-agent-token
   CORS_ORIGIN=*
   ```

4. **Start the backend:**

   ```bash
   npm run dev
   ```

5. **Test backend:**

   ```bash
   curl https://system-health-monitor-arqh.onrender.com/health
   ```

---

### Frontend (React + Vite)

1. **Navigate to frontend folder:**

   ```bash
   cd ../frontend
   npm install
   ```

2. **Environment variables:**

   ```
   ```

VITE\_API\_BASE\_URL=[https://system-health-monitor-arqh.onrender.com/api](https://system-health-monitor-arqh.onrender.com/api)

````

3. **Run locally:**
   ```bash
   npm run dev
````

4. **Deploy to Netlify:**

   * Build command: `npm run build`
   * Publish directory: `dist`
   * Add environment variable `VITE_API_BASE_URL`

---


# Example cron for every 30 minutes

\*/30 \* \* \* \* /path/to/main

```

---

### Utility (Python)
### Checking Friend's System Health

1. Package the utility as an executable with `API_URL` pointing to deployed backend:
```

[https://system-health-monitor-arqh.onrender.com/api/report](https://system-health-monitor-arqh.onrender.com/api/report)

```

2. Send executable to friend.
3. Friend runs it once.
4. System health data automatically appears in your **frontend dashboard**.

**Note:** The utility must run on the target machine — there is no way to collect system health remotely without it.

---

## Deployment Summary

| Component | Deployment |
|-----------|-----------|
| Backend   | Render (Node.js service) |
| Frontend  | Netlify (React + Vite) |
| Utility   | Local |

---

## Links

- Backend API: `https://system-health-monitor-arqh.onrender.com`
- Frontend Dashboard: (deployed Netlify URL)
- GitHub Repo: `https://github.com/praneethrms04/system-health-monitor`

---

## Notes

- Python utility collects:
  - Disk encryption status
  - OS update status
  - Antivirus presence/status
  - Sleep/inactivity settings
- Sends updates periodically to backend.
- Backend stores machine snapshots and history.
- Frontend shows list of machines, latest status, issues, and filters.

```
