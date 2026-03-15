# Changelog

All notable changes to the Personal Finance Dashboard are documented here.


## [Unreleased]
> Features planned or in progress — not yet in a release

- [ ] Config file integration (rubrica names, custom categories, tracked recurring items)
- [ ] In-app expense entry writing back to Excel/CSV database
- [ ] PDF/PNG export of any view
- [ ] Multi-file comparison (year over year across separate files)
- [ ] Budget targets per category with alert indicators
- [ ] Shared/split expense tracking
- [ ] Dark/light mode toggle

---

## [0.4.0] — 2025-03-15

### Added
- **Occasion toggle** in Overview, Monthly, and Category Deep Dive — exclude extraordinary trip/event spending from core metrics to see "normal life" baseline
- **Category Deep Dive** tab — generalized from Food & Dining; select any spending category (Housing, Transport, Food, Leisure, Travel, Personal, Debt) and get the same detailed breakdown: KPIs, monthly stacked chart, top vendor/description table
- **Occasions drill-down** in Analysis tab — click any occasion/trip row to expand and see every individual transaction within it
- **Savings in €** instead of rate on Monthly tab — net amount saved/overspent each month is more actionable than a percentage
- **Subcategory drill-down** on Monthly tab — clicking a category in the month detail expands it to show all subcategories (e.g., click Food → see Groceries / Dining Out / Snacks)
- **Recurring configuration** — mark items as Subscription, Fixed, or Variable in the Recurring tab; preference saved to localStorage
- **Rich insights panel** on Overview — 8+ computed insights: biggest month, worst category growth, subscription creep, weekend vs weekday ratio, top occasion cost, savings streak
- **Key personal finance metrics** added: Fixed Cost Ratio, Discretionary Spending, Subscription % of income, 3-month spending trend (up/down/flat)

### Changed
- **Overview** — removed income vs expense bar chart; replaced with KPI cards for Fixed Cost Ratio, Discretionary %, Top Growing Category, and a sparkline-style mini trend per category
- **Analysis tab** — removed Day of Week section (not actionable enough); added per-category analysis panels with top vendors, frequency, and avg transaction
- **Monthly tab** — savings display changed from rate (%) to net € value; negative months shown in red
- **Upload screen** — now accepts both `.xlsx` and `.csv`; auto-detects column structure from either format

### Fixed
- MINIFS/MAXIFS formula errors no longer affect recurring items with no data
- Year selector now correctly updates all charts on change
- Occasion tags now show consistently across tabs

---

## [0.3.0] — 2025-03-10

### Added
- **Recurring & Subscriptions tab** — auto-detects items appearing 3+ times; splits into Fixed Costs, Digital Subscriptions, and High-Frequency sections; shows 6M/12M totals and ACTIVE/LAPSED/STOPPED badge computed from last transaction date
- **Spending Analysis tab** — day-of-week breakdown with bar chart, occasions & trips table, category × month heatmap with per-row color intensity
- **Transactions tab** — full searchable/filterable/sortable table with pagination; filters by text, category, occasion, type (income/expense)
- **Year selector** in top bar — changing year re-renders all tabs instantly
- Income entries highlighted in green in transaction table

### Changed
- Navigation restructured into 6 tabs: Overview, Monthly, Food & Dining, Recurring, Analysis, Transactions
- Top bar now shows live total expenses and transaction count for selected year

### Fixed
- Date parsing handles both Excel serial dates and ISO strings
- Amount parsing handles Portuguese decimal format (comma as decimal separator)

---

## [0.2.0] — 2025-03-05

### Added
- **Monthly tab** — 12-month grid with expense/income/savings rate per month; click any month to drill into category breakdown and top transactions; savings rate trend line chart
- **Food & Dining tab** — dedicated food analytics: KPI cards for Groceries / Dining Out / Snacks / Total Food; monthly stacked bar chart; top grocery stores and dining spots ranked by spend
- Drag-and-drop file upload
- Progress bar with parsing feedback
- Chart.js integration for bar, line, and doughnut charts

### Changed
- Overview category breakdown now uses donut chart instead of plain list
- KPI cards now have colored top accent borders per category

---

## [0.1.0] — 2025-03-01 — Initial Release

### Added
- **Upload screen** — drop or browse for `.xlsx` file; auto-detects RAW 2025 sheet vs Database sheet column structure
- **Overview tab** with 8 KPI cards: Total Expenses, Total Income, Net Savings, Avg/Month, Top Category, Biggest Single Transaction, Transaction Count, Travel Total
- **Category breakdown** — spending grouped by overview category with totals
- **Basic insights** — 4 auto-generated text insights from the data
- Monthly bar chart (Income vs Expenses)
- Parses both original `PERSONAL.xlsx` RAW sheet format (Portuguese column names) and `PERSONAL_V5.xlsx` Database sheet format
- Support for years 2025 and 2026 in the same dataset
- Sidebar navigation structure (tabs not yet all implemented)

---

## Development Notes

### Branch Strategy
```
main          ← stable releases only
dev           ← active development, merged to main on release
feature/*     ← individual features (e.g. feature/config-file, feature/csv-export)
fix/*         ← bug fixes
```

### Release Process
1. Work on `dev` or a `feature/*` branch
2. Update `CHANGELOG.md` — move items from `[Unreleased]` to a new version section
3. Bump version number in `finance-dashboard.html` (top comment block)
4. Open PR from `dev` → `main`
5. Tag the merge commit: `git tag v0.4.0 && git push --tags`

### Files in This Repo
```
/
├── finance-dashboard.html   ← main single-file web app
├── CHANGELOG.md             ← this file
├── config.json              ← user configuration (categories, tracked items, etc.)
├── README.md                ← setup instructions
└── data/
    └── PERSONAL.xlsx        ← source-of-truth database (gitignored if private)
```

### Config File Design (v0.5.0 target)
The `config.json` will drive:
- Custom category names and icons
- Which recurring items to track and classify (subscription vs fixed)
- Whether to exclude occasions from core metrics by default
- Budget targets per category
- Preferred currency symbol and locale
- Income sources to include/exclude

The web app will have a **Config tab** where you can edit all of these in-app
and export the updated `config.json` to save locally.
