# GigaPulse - Quick Start Guide

## 🚀 Start the Application

### Method 1: Double-click (Easiest)
1. Navigate to: `c:\Users\ftrhack176\Desktop\GIGAPULSE\gigapulse-demo`
2. Double-click `run_app.bat`
3. Wait for the browser to open automatically

### Method 2: Command Line
```bash
cd c:\Users\ftrhack176\Desktop\GIGAPULSE\gigapulse-demo
run_app.bat
```

## 🔐 Login

The app will open at: **http://localhost:8000**

### Demo Credentials (any of these work):
- **Username:** `admin` | **Password:** `gigapulse`
- **Username:** `demo` | **Password:** `gigapulse`
- **Username:** `noc` | **Password:** `gigapulse`
- **Username:** `engineer` | **Password:** `gigapulse`

## 🎯 What You'll See

### 1. Login Page
- Beautiful animated GigaPulse logo with pulsing effects
- Particle background animation
- Glassmorphic design
- Demo credentials shown on the page

### 2. Main Dashboard (after login)
- **Header:** Logo, status, username, logout button
- **Left Sidebar:** AI Agents, Alerts, and Metrics tabs
- **Center:** Interactive network graph with D3.js
- **Bottom Right:** AI chat panel
- **Controls:** Reset view, pause, expand all, analytics

## 📊 Features to Explore

### Network Graph
- **Click nodes** to see detailed information
- **Drag nodes** to reposition them
- **Zoom** with mouse wheel
- **Expand nodes** to see child entities
- **Color coding:**
  - 🔥 Red = Outages (critical)
  - 🏢 Gold = CLLI locations
  - 🔌 Orange = Infrastructure
  - 💻 Purple = Equipment
  - 👥 Blue = Customers
  - 👷 Yellow = Repair crews

### AI Agents (Left Sidebar)
Click on any agent to activate their workflow:
1. **Circuit Charlie** - Infrastructure diagnostics
2. **Priority Parker** - Alert triage
3. **Dispatch Dana** - Work order management
4. **Sophie** - Customer communications
5. **Louie** - Remote resolution

### Scenario Buttons
Switch between different operational modes:
- **Live Outage** - Active incident response
- **Normal Ops** - Standard monitoring
- **Churn Analysis** - Customer retention

### AI Chat
Ask questions like:
- "What's the current outage status?"
- "Show me churn predictions"
- "Which customers are at high risk?"
- "Can we resolve this remotely?"

## 🛑 Stop the Application

Press `Ctrl+C` in the terminal window where the server is running.

## 🔄 Logout

Click the **Logout** button in the top-right header to end your session and return to the login page.

## 📁 File Structure

```
gigapulse-demo/
├── frontend/
│   ├── login.html     ← Entry point (animated login)
│   └── index.html     ← Main app (enhanced_v4 UI)
├── backend/
│   ├── main.py        ← Server (routes: / = login, /app = main)
│   └── ...
└── run_app.bat        ← Start script
```

## 🎨 UI Highlights

### Login Page Features
- Animated pulsing logo
- Network particle effects  
- Glassmorphic card design
- Smooth transitions
- Responsive design

### Main Dashboard Features
- Real-time network graph
- Interactive node expansion
- Workflow chain visualization
- Live metrics and alerts
- Predictive analytics
- AI chat interface
- Modern dark theme

## 🐛 Troubleshooting

### Port Already in Use
If you see "Address already in use" error:
```bash
# Find and kill the process using port 8000
netstat -ano | findstr :8000
taskkill /PID <process_id> /F
```

### Database Issues
Delete the database and restart:
```bash
del backend\gigapulse.db
run_app.bat
```

### Login Redirects Back
- Clear browser cache
- Check browser console for errors
- Ensure sessionStorage is enabled

### Graph Not Loading
- Refresh the page
- Check if backend is running
- Open browser DevTools (F12) and check Console

## 📖 Full Documentation

See `README.md` in the `gigapulse-demo` folder for complete documentation.

---

**Current Status:** ✅ Fully Integrated and Running
- Login system: ✅ Active
- Main UI: ✅ Enhanced v4
- Backend: ✅ FastAPI server
- Database: ✅ Seeded with demo data
- Authentication: ✅ Session-based

**App is ready to use!** 🎉
