# Teacher Rating Monitoring System

A lightweight, client-side dashboard for tracking teacher star ratings, computing
low-star rates against a target threshold, and generating weekly/monthly reports.
No backend or build step required — it's plain HTML, CSS, and JavaScript, and all
data is stored in the browser's `localStorage`.

## Features

- **Dashboard** — monthly KPI cards, a weekly low-star-rate chart, and a monthly
  per-teacher summary table.
- **Rating Records** — add/search/delete individual dated star ratings.
- **Teacher Star Totals** — enter aggregate 1–5 star counts per teacher for a
  month directly (useful when totals are reported rather than logged one by one).
- **Weekly Report** — Sunday–Saturday breakdown for every week touching the
  selected month.
- **Monthly Report** — full monthly summary, printable to PDF.
- **Teacher Performance** — per-teacher drill-down across all weeks in a month.
- **Action Plan & Target** — log follow-up plans for teachers below target,
  with status tracking (Pending / In Progress / Completed).
- **Reports / Export** — export the selected month's ratings as CSV, or print
  any report page to PDF.
- **Settings** — set the target low-star rate, manage the teacher list, and
  back up/restore all data as JSON.

## Project structure

```
teacher-rating-monitoring-system/
├── index.html      # Page structure/layout
├── css/
│   └── style.css   # All styling
├── js/
│   └── app.js       # App state, calculations, and rendering logic
└── README.md
```

## Running it locally

No install or build step is needed. Either:

- Open `index.html` directly in a browser, or
- Serve the folder with any static server, e.g.:
  ```bash
  npx serve .
  # or
  python3 -m http.server 8080
  ```
  then visit `http://localhost:8080`.

## Deploying with GitHub Pages

1. Push this repository to GitHub.
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to `Deploy from a branch`,
   pick your default branch (e.g. `main`) and the `/ (root)` folder.
4. Save — GitHub will publish the site at
   `https://<your-username>.github.io/<repo-name>/`.

## Data & storage

All data (teachers, ratings, action plans, and the target rate) is kept in the
browser's `localStorage` under the key `teacherRatingSystemV1`. This means:

- Data is per-browser/per-device — it does not sync across machines.
- Clearing browser data or `localStorage` will erase it.
- Use **Settings → Data Backup → Download Backup JSON** regularly to keep a
  copy, and **Reports → Export Rating Records CSV** for spreadsheet use.

## Low-star rate calculation

For a given set of ratings:

- **Low stars** = count of 1★, 2★, 3★ ratings
- **High stars** = count of 4★, 5★ ratings
- **Low-star rate** = Low stars ÷ High stars (shown as a percentage)
- **Status** = `PASS` if the rate is at/below the target rate, otherwise `FAIL`
- **Additional high stars needed** = the number of extra high-star ratings
  needed to bring the rate back to target

## License

No license file is included yet — add one (e.g. MIT) if you plan to share or
open-source this repository.
