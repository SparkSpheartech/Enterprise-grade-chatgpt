# GigaPulse Webgraph Walkthrough

## Overview
This walkthrough demonstrates the "Fiber Outage Webgraph" visualization, now upgraded with an Enhanced UI (v4) and fully integrated with the Python FastAPI backend.

## Features
1.  **Enhanced UI**: Modern, dark-themed interface with "Deep End Louie" AI agent, predictive analytics, and workflow visualization.
2.  **Live Data**: Connects to `http://localhost:8000/api/graph/data` to fetch real-time network topology from the SQLite database.
3.  **Data Enrichment**: The frontend automatically enriches the backend data with simulated metrics (Churn Risk, Remote Resolution Status) to demonstrate the advanced UI features.
4.  **Animated Logo**: Custom GigaPulse animated logo integrated into the header.

## Verification Steps
1.  **Backend**: Ensure the Python backend is running (`python main.py`).
2.  **Frontend**: Open `gigapulse-demo/frontend/index.html` in a web browser.
3.  **Interaction**:
    *   **Graph**: Zoom and pan the network graph.
    *   **Details**: Click on nodes (e.g., "OUT-2024-CA-001") to see the sidebar details and "Louie's Tips".
    *   **AI Agents**: Click on the "AI Agents" tab in the sidebar to see the workflow status.
    *   **Chat**: Interact with the chat panel (simulated).

## Technical Details
*   **Frontend**: Vanilla JS + D3.js (v7).
*   **Backend**: Python FastAPI + SQLAlchemy + SQLite.
*   **Data Flow**: Backend serves raw entity data -> Frontend fetches JSON -> Frontend enriches data -> D3 renders graph.
