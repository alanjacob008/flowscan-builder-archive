# FlowScan Builder Archive

A single source of truth for daily FlowScan "builder-fills" data across multiple builders.

## 📦 Repository Structure

```
data/
├── combined/
│   └── daily_summary_all.json  # All builders' daily summaries combined
└── <builder>/                  # One folder per builder
    ├── YYYYMMDD.json           # Raw API response for that date
    ├── daily_summary.json      # [{ date, revenue, volume, tradecount, uniqueusers }]
    ├── user_data.json          # Aggregated per-user stats with active days
    └── failed_dates.json       # Dates that failed to fetch
```

## 🚀 Getting Started

1. **Inspect** any builder’s `data/<builder>/daily_summary.json` for daily metrics.
2. **Use** `data/combined/daily_summary_all.json` to see all builders in one file.
3. **Analyze** or visualize in your preferred tool.

## ⚙️ Automation

A GitHub Action runs nightly at 00:00 UTC to

* Fetch new daily JSONs only for missing dates
* Update `daily_summary.json` and `user_data.json`
* Rebuild the combined summary
* Commit changes back to this repo

---

*Why?* To keep a versioned, centralized history of builder-fill data for reliable trend analysis.
