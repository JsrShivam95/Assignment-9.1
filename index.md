              HTML

<!DOCTYPE html>
<html lang="en">
<head>
  <!-- Step 2: Critical viewport meta tag to enable mobile scaling -->
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Assignment 9.1 — Mobile-First Responsive Dashboard</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <div class="dashboard-shell">

    <!-- Step 1: Header / Top Navigation -->
    <header class="app-header">
      <div class="brand">
        <span class="brand-logo">⚡</span>
        <span class="brand-title">ApexCloud</span>
      </div>
      <div class="header-user">
        <span class="user-name">Sarah Chen</span>
        <div class="user-avatar">SC</div>
      </div>
    </header>

    <!-- Step 1: Primary Navigation Bar -->
    <nav class="app-nav">
      <ul class="nav-list">
        <li><a href="#overview" class="active">Overview</a></li>
        <li><a href="#analytics">Analytics</a></li>
        <li><a href="#deployments">Deploys</a></li>
        <li><a href="#settings">Settings</a></li>
      </ul>
    </nav>

    <!-- Step 1: Main Content Container -->
    <main class="app-main">
      <section class="page-title">
        <h1>Infrastructure Dashboard</h1>
        <p>Live health and workload telemetry across active clusters.</p>
      </section>

      <!-- Metric Cards -->
      <section class="stats-grid">
        <article class="stat-card">
          <span class="stat-label">Active Pods</span>
          <p class="stat-value">1,428</p>
          <span class="stat-trend positive">+12.5% this week</span>
        </article>

        <article class="stat-card">
          <span class="stat-label">CPU Utilization</span>
          <p class="stat-value">64.2%</p>
          <span class="stat-trend neutral">Stable</span>
        </article>

        <article class="stat-card">
          <span class="stat-label">Average Latency</span>
          <p class="stat-value">32ms</p>
          <span class="stat-trend positive">-4ms improvement</span>
        </article>

        <article class="stat-card">
          <span class="stat-label">Error Rate</span>
          <p class="stat-value">0.02%</p>
          <span class="stat-trend negative">+0.01% drift</span>
        </article>
      </section>

      <!-- Activity Feed / Secondary Content -->
      <section class="activity-feed">
        <h2>Recent Cluster Deployments</h2>
        <div class="event-item">
          <div class="event-bullet success"></div>
          <div class="event-details">
            <p class="event-title"><strong>us-east-1</strong> worker-service deployed</p>
            <span class="event-time">5 minutes ago</span>
          </div>
        </div>

        <div class="event-item">
          <div class="event-bullet success"></div>
          <div class="event-details">
            <p class="event-title"><strong>eu-west-1</strong> api-gateway scale-out (+4)</p>
            <span class="event-time">22 minutes ago</span>
          </div>
        </div>

        <div class="event-item">
          <div class="event-bullet warning"></div>
          <div class="event-details">
            <p class="event-title"><strong>ap-south-1</strong> memory limit threshold 85%</p>
            <span class="event-time">48 minutes ago</span>
          </div>
        </div>
      </section>
    </main>

  </div>

</body>
</html>


                      CSS


/* --- Global Reset & Mobile-First Baseline --- */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --primary: #2563eb;
  --bg-page: #f8fafc;
  --bg-surface: #ffffff;
  --bg-nav: #0f172a;
  --border: #e2e8f0;
  --text-main: #0f172a;
  --text-muted: #64748b;
  --success: #16a34a;
  --warning: #d97706;
  --danger: #dc2626;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  color: var(--text-main);
  background-color: var(--bg-page);
  line-height: 1.5;
  /* Step 7: Overflow prevention on the viewport root */
  width: 100%;
  overflow-x: hidden;
}

/* ================= STEP 3: MOBILE-FIRST STYLES (< 768px) ================= */
/* Default single-column vertical flow designed primarily for small screens */

.dashboard-shell {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  width: 100%;
}

/* Header */
.app-header {
  background-color: var(--bg-surface);
  border-bottom: 1px solid var(--border);
  padding: 0.85rem 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: sticky;
  top: 0;
  z-index: 100;
}

.brand {
  display: flex;
  align-items: center;
  gap: 0.4rem;
  font-size: 1.15rem;
  font-weight: 800;
}

.brand-title {
  letter-spacing: -0.02em;
}

.header-user {
  display: flex;
  align-items: center;
  gap: 0.6rem;
}

.user-name {
  display: none; /* Hide full user text on compact mobile screens */
}

.user-avatar {
  width: 34px;
  height: 34px;
  border-radius: 50%;
  background-color: #dbeafe;
  color: var(--primary);
  font-size: 0.8rem;
  font-weight: 700;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Mobile Nav: Horizontal scroll rail */
.app-nav {
  background-color: var(--bg-nav);
  padding: 0.5rem 1rem;
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
}

.nav-list {
  display: flex;
  gap: 0.75rem;
  list-style: none;
  white-space: nowrap;
}

.nav-list a {
  display: block;
  color: #94a3b8;
  text-decoration: none;
  font-size: 0.85rem;
  font-weight: 500;
  padding: 0.4rem 0.75rem;
  border-radius: 6px;
  transition: all 0.2s ease;
}

.nav-list a:hover,
.nav-list a.active {
  background-color: #1e293b;
  color: #ffffff;
}

/* Main Content Area */
.app-main {
  padding: 1.25rem 1rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  flex: 1;
}

.page-title h1 {
  font-size: 1.45rem;
  font-weight: 800;
  letter-spacing: -0.02em;
}

.page-title p {
  color: var(--text-muted);
  font-size: 0.875rem;
  margin-top: 0.25rem;
}

/* Stats: Single column on narrow screens */
.stats-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
}

.stat-card {
  background-color: var(--bg-surface);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 1.25rem;
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
}

.stat-label {
  font-size: 0.8rem;
  font-weight: 600;
  color: var(--text-muted);
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.stat-value {
  font-size: 1.75rem;
  font-weight: 800;
  letter-spacing: -0.02em;
}

.stat-trend {
  font-size: 0.8rem;
  font-weight: 600;
}

.stat-trend.positive { color: var(--success); }
.stat-trend.neutral  { color: var(--text-muted); }
.stat-trend.negative { color: var(--danger); }

/* Activity Section */
.activity-feed {
  background-color: var(--bg-surface);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 1.25rem;
}

.activity-feed h2 {
  font-size: 1.05rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.event-item {
  display: flex;
  align-items: flex-start;
  gap: 0.75rem;
  padding: 0.75rem 0;
  border-bottom: 1px solid var(--border);
}

.event-item:last-child {
  border-bottom: none;
  padding-bottom: 0;
}

.event-bullet {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  margin-top: 0.35rem;
  flex-shrink: 0;
}

.event-bullet.success { background-color: var(--success); }
.event-bullet.warning { background-color: var(--warning); }

.event-title {
  font-size: 0.875rem;
  color: #334155;
  word-break: break-word; /* Step 7: prevent text breaking layout */
}

.event-time {
  font-size: 0.75rem;
  color: var(--text-muted);
}


/* ================= STEP 4 & 5: BREAKPOINT 1 (TABLET >= 768px) ================= */
@media (min-width: 768px) {
  .app-header {
    padding: 1rem 2rem;
  }

  .user-name {
    display: inline-block;
    font-size: 0.9rem;
    font-weight: 600;
  }

  .app-main {
    padding: 2rem;
  }

  .page-title h1 {
    font-size: 1.85rem;
  }

  /* Two-column stat grid on tablets */
  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 1.25rem;
  }
}


/* ================= STEP 4 & 5: BREAKPOINT 2 (DESKTOP >= 1024px) ================= */
@media (min-width: 1024px) {
  /* Converts single-column shell to a true 2D desktop grid */
  .dashboard-shell {
    display: grid;
    grid-template-columns: 240px 1fr;
    grid-template-rows: 68px 1fr;
    grid-template-areas:
      "header header"
      "sidebar main";
  }

  .app-header {
    grid-area: header;
    padding: 0 2rem;
  }

  .app-nav {
    grid-area: sidebar;
    padding: 2rem 1.25rem;
    overflow-x: visible;
  }

  .nav-list {
    flex-direction: column;
    gap: 0.5rem;
  }

  .nav-list a {
    font-size: 0.95rem;
    padding: 0.65rem 1rem;
  }

  .app-main {
    grid-area: main;
    padding: 2.5rem;
    max-width: 1280px;
  }

  /* Four columns in a single horizontal row for desktop */
  .stats-grid {
    grid-template-columns: repeat(4, 1fr);
    gap: 1.5rem;
  }
}