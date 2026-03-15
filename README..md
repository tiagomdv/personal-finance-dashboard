**Dynamic Offline Personal Finance Dashboard**

A modern, fully offline, single-file interactive web application that transforms your expense data into professional-grade insights, visualizations, and analytics — all running locally in your browser.

Built around a clean three-file architecture:
- **`finance-dashboard.html`** — the complete interactive dashboard  
- **`PERSONAL.xlsx`** — your single source of truth database  
- **`config.json`** — user-configurable settings  

**You maintain your data in Excel. The dashboard gives you clarity.**

---

## ✨ Highlights

- 100 % offline – no account, no server, no data leaves your computer  
- Instant upload of your existing `PERSONAL.xlsx` (or CSV)  
- Fully dynamic: change year, toggle occasions, or update config → everything recalculates live  
- Professional dark-themed UI with Chart.js visualizations  
- Designed specifically for users who want both simplicity (Excel as source of truth) and power (interactive web experience)

---


## 🚀 Quick Start

1. Download the latest release:
   - `finance-dashboard.html`
   - `CHANGELOG.md` (recommended)
   - `config.json` (optional – start with the template)

2. Place your `PERSONAL.xlsx` in the same folder (or anywhere convenient).

3. Double-click `finance-dashboard.html` to open it in any modern browser.

4. Drag & drop your `PERSONAL.xlsx` (or click to browse).  
   The dashboard instantly parses your data and renders all views.

**No installation. No dependencies. Works offline after the first load.**

---

## 🗂️ Project Architecture (The Ideal Dynamic Setup)

| File                  | Purpose                                      | Maintained By          | Format     |
|-----------------------|----------------------------------------------|------------------------|------------|
| `finance-dashboard.html` | Full interactive web application            | You (update when new version released) | Single HTML |
| `PERSONAL.xlsx`       | Single source of truth – all your transactions | **You**                | Excel      |
| `config.json`         | Custom categories, recurring rules, budgets, preferences | You (or edit inside the app in future) | JSON       |

**Workflow**  
Update expenses → save `PERSONAL.xlsx` → open/reload the HTML file → drag your Excel → enjoy fresh, live insights.  
The app reads both your database and `config.json` in real time.

---

## 📊 Current Features (v0.4.0)

### Overview
- Live KPI cards: Total Expenses, Income, Net Savings, Avg/Month, Fixed Cost Ratio, Discretionary %, Subscription % of Income, 3-month trend
- Category sparklines (12-month trend)
- Rich insights panel with 8+ actionable observations
- **Occasion Toggle** – exclude extraordinary trips/events from all core metrics

### Monthly
- Full-year grid with Expenses, Income, and **net savings in €** (green/red)
- Click any month → category breakdown with subcategory drill-down
- Net balance bar chart

### Category Deep Dive
- Switch between Housing, Transport, Food, Leisure, Travel, Personal, Debt
- Per-category KPIs, monthly stacked charts, top vendors, and transaction list

### Recurring
- Auto-detected Fixed Costs, Subscriptions & Variable items
- Live metrics: Start Date, Last Date, Avg/Month, 6M/12M totals
- Status badges (● ACTIVE / ◐ LAPSED / ○ STOPPED) that update daily
- Manual classification with localStorage persistence

### Analysis
- Occasions & Trips with full expandable drill-down
- Per-category analysis panels
- Category × Month heatmap (per-row color scaling)
- Top 10 single transactions

### Transactions
- Fully searchable, sortable, filterable table with pagination
- Income rows highlighted

**All views update instantly** when you change the year selector or toggle the occasion filter.

---

## 🛠️ Supported Data Formats

- Excel `.xlsx` (recommended) – works with both raw sheets and the improved Database sheet
- CSV (auto-detected column structure)
- Multiple years in one file (2025, 2026, …)
- Portuguese decimal format and Excel serial dates fully supported

---

## 🗺️ Roadmap & Future Features

See [CHANGELOG.md](CHANGELOG.md) for detailed history and the `[Unreleased]` section.

**Planned for v0.5.0+**
- Full in-app `config.json` editor (add/edit categories, set budgets, define recurring rules)
- In-app expense entry that writes back to your Excel/CSV file
- Budget targets with variance alerts and visual indicators
- PDF/PNG export of any view or report
- Dark/Light mode toggle
- Multi-file comparison (year-over-year across separate Excel files)
- Shared/split expense support
- Advanced filters and custom reports

---
