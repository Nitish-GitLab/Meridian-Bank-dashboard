# Meridian Bank – Customer Analytics Dashboard

An interactive, single-page **banking customer analytics dashboard** built with HTML, CSS, JavaScript and Chart.js. It runs entirely in the browser, with no backend, no build step and no installation.

> **Data note:** the bundled dataset is **800 synthetic customers** generated for demonstration. It is not real bank or customer data. You can load your own CSV (see [Using your own data](#using-your-own-data)).

## Preview

Add a screenshot after you run the project:

```
![Dashboard overview](screenshots/overview.png)
```

## Features

- **Five pages:** Executive Overview, Customer Segmentation, Financial Analysis, Risk & Credit Analysis and Customer Data Explorer.
- **Eight dropdown filters:** Time period, Region/State/City, Customer segment, Age group, Income band, Gender, Account type and Risk category. Every filter updates the KPI cards, all 14 charts and the data table at once. A **Reset filters** button clears them.
- **Six KPI cards:** Customers, Total deposits, Average balance, Average credit score, Active customers and High-risk share. Currency is shown in INR (₹) with lakh/crore units.
- **14 charts** (Chart.js): line, bar, horizontal bar and doughnut charts.
- **Customer Data Explorer:** searchable, sortable, paginated table with risk-category pills and **Export filtered CSV**.
- **Load your CSV:** upload a file with the columns below and the whole dashboard rebuilds from it.
- **Design:** navy sidebar and header with a glass-tower skyline illustration, glassmorphism cards, responsive layout, keyboard focus styles and automatic dark mode.

## Tech stack

| Layer | Technology |
|---|---|
| Markup / styling | HTML5, CSS3 (grid, custom properties, backdrop-filter) |
| Logic | Vanilla JavaScript (ES6) |
| Charts | [Chart.js 4.4.1](https://www.chartjs.org/) via CDN |

## Run it

1. Download or clone the repository.
2. Open `index.html` in any modern browser (needs internet access once to load Chart.js from the CDN).

**Publish on GitHub Pages:** *Settings → Pages → Deploy from a branch → `main` / root*. Your live link will be `https://<your-username>.github.io/<repo-name>/`.

## Using your own data

Click **Load your CSV** in the sidebar. The first row must contain these headers (case and spaces are ignored):

| Column | Meaning |
|---|---|
| Customer ID | Unique customer identifier |
| City, State | Location (feeds the Region/State/City filter) |
| Segment | e.g. Retail, Premium |
| Age | Number |
| Gender | Text |
| Annual Income | Annual income in ₹ (number) |
| Account Type | e.g. Savings, Current |
| Balance | Account balance in ₹ (number) |
| Credit Score | Number (300–900) |
| Joined | Date in `YYYY-MM-DD` format |
| Defaulted *(optional)* | `1`/`0`, `yes`/`no` |
| Active *(optional)* | `1`/`0`, `yes`/`no` |

A ready-to-use example is in `data/sample_customers.csv`. If `Defaulted` or `Active` is missing, the dashboard says so: the default rate then shows 0% and the active share 100%.

## Metric definitions

| Metric | Definition |
|---|---|
| Customers | Number of rows after filters |
| Total deposits | Sum of Balance |
| Average balance | Total deposits ÷ Customers |
| Active customers | Share of customers with Active = yes |
| Risk category | Derived from Credit Score: **Low** ≥ 750, **Medium** 650–749, **High** < 650 |
| High-risk share | Customers in the High category ÷ Customers |
| Default rate | Share of customers with Defaulted = yes |
| Age group / Income band | Fixed bins: 18–25, 26–35, 36–45, 46–60, 60+; below ₹3L, ₹3–6L, ₹6–12L, ₹12–25L, ₹25L+ |

## Project structure

```
banking-customer-analytics-dashboard/
├── index.html                  # the whole dashboard (HTML + CSS + JS)
├── data/
│   └── sample_customers.csv    # 800 synthetic customers
├── screenshots/                # add your screenshots here
├── README.md
└── LICENSE
```

## Limitations

- The background is a drawn skyline illustration, not a photograph. To use your own photo, replace the `--img` value in the script with a base64 data URI.
- Everything runs in the browser, so very large files (hundreds of thousands of rows) will be slow.
- Risk category is derived from credit score only; it is not a full credit-risk model.
- Region/State/City is a single combined dropdown (state or city, not both at once).

## Possible next steps

- Connect to a database (for example MySQL) through a small API.
- Add a date-range picker and month-over-month comparison.
- Add unit tests for the aggregation functions.

## License

MIT – see `LICENSE`.

## Author

Your Name · [LinkedIn](https://linkedin.com/in/your-profile) · [GitHub](https://github.com/your-username)
