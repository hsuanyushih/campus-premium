# Campus Premium

This repository is your starting point for the Home Sales case. It already holds the dataset, its description sheet, project instructions for your AI coding agent, and outlines of the README and agent log that the case asks for.

1. **Turn on GitHub Pages.** In this repository, open **Settings**, then **Pages**. Under "Build and deployment," set **Source** to **GitHub Actions**. GitHub may suggest workflows to add. Skip them: this repository already has one, `.github/workflows/pages.yml`.
2. **Publish for the first time.** Open the **Actions** tab, choose **Publish site to GitHub Pages** in the sidebar, click **Run workflow**, then click **Run workflow** again to confirm. If the tab already shows a failed run from when you created the repository, that's expected: Pages wasn't turned on yet. When the new run shows a green check, your site is at `https://your-username.github.io/your-repo-name/`. It shows a placeholder page until you replace `index.html`.

    From then on, every push to the main branch publishes the site within a few minutes. If the live site doesn't show a change, open the **Actions** tab. A red X means the publish failed, and the run's log says why.
3. **Open the repository in your AI coding agent.** Its project instructions are in `AGENTS.md`. If your agent reads its instructions from a file with a different name, check its documentation and copy `AGENTS.md` to that name. Add to the instructions as you learn what your agent needs.
4. **Read `docs/data_description_sheet.md`** before you ask the agent for any analysis.
5. **Build in small steps,** as the setup guide describes. Add an entry to `AGENT_LOG.md` each time you work with the agent.
6. **Fill in every section below** before you submit.

| Path | What it is |
|---|---|
| `index.html` | The site: a university dropdown, number cards, a scatter plot, a bar chart and a budget slider. |
| `data/college_town_home_sales.csv` | The dataset, version 1.0: 35,442 rows. Your site reads this file. |
| `data/college_town_home_sales.xlsx`, `.sqlite`, `.duckdb`, `.parquet` | The same data in Excel, SQLite, DuckDB and Parquet formats, with identical values |
| `docs/data_description_sheet.md` | What every column means, and five problems in the data |
| `AGENTS.md` | Project instructions for your AI coding agent |
| `AGENT_LOG.md` | Your agent log |
| `scripts/` | Scripts that make smaller data files for the site |
| `.github/workflows/pages.yml` | Publishes the site to GitHub Pages each time you push to main. It publishes your files as they are. If you switch to a framework that needs a build step, have your agent update it. |

Don't edit any of the five dataset files. Your site needs only the CSV file. The other formats make it easier to check numbers a second way, for example with a pivot table in Excel or a SQL query on the SQLite file. In SQLite and DuckDB, the table is named `home_sales`.

## What this site is for

Campus Premium asks how home prices in college towns change with distance to campus. It covers the 11 universities in the College-town home sales dataset. For each campus, it shows:

- the median sale price, the median price per square foot, and the median number of days from listing to contract;
- how sale prices spread out by distance to campus;
- how many sales a given budget would have covered, and what those homes were like.

The audience is anyone comparing college-town housing: prospective buyers, students and families, and researchers.

## Live site

https://hsuanyushih.github.io/campus-premium/

## Data notes

The site reads `data/college_town_home_sales.csv` in the browser and computes every figure from it. No number is typed in by hand.

**Rows left out.** Sales under $10,000 are excluded everywhere on the site: 40 of the 35,442 rows. The other 35,402 sales are used. This is the site's own rule. The description sheet's city table uses a $1,000 cutoff, so some of its medians differ from ours. For example, Chapel Hill is $735,000 in the sheet and $725,000 here.

**How each figure is defined**

- **Median sale price:** the median of `sale_price` for the university's sales, rounded to whole dollars. The bar chart and the number card use the same figure.
- **Median price per sq ft:** the median of `sale_price` divided by `living_area_sqft`. Sales with a blank or zero living area are left out of this figure only.
- **Median days from listing to contract:** the median of `contract_date` minus `list_date`, in days. Sales missing either date are left out of this figure only. Days from listing to closing are not used.
- **Scatter plot:** one dot per sale. Across is `miles_to_campus`, up is `sale_price`. The price axis stops at the university's 99th percentile, so a few very high sales do not flatten the rest. The page says how many higher-priced sales are not drawn. The dark line is the median price in each half-mile band, drawn only where a band has at least 10 sales.
- **Budget slider:** from $100,000 to $1,000,000. It shows the share of the university's sales at or under the chosen price, and the medians of living area, bedrooms and distance to campus for those sales. Sales above $1,000,000 are not in the share. These are past sales, not homes for sale today.

**Other points from the description sheet**

- `home_type` is not used, because the sheet says it is unreliable.
- Street addresses are not used as keys. `listing_id` is.
- The figures are as the source reported them. They have not been checked against county records.

_Replace this line. Say which rows you left out and why, and how each figure on the site is defined. "Five things that will bite you" in the description sheet lists the problems to cover._

## Tools we used

Claude Code, an AI coding agent made by Anthropic, wrote and edited the site under the instructions in `AGENTS.md`. The site is plain HTML, CSS and JavaScript, with no framework or build step. Two fonts come from Google Fonts: Source Serif 4 and EB Garamond. Python was used to recompute the medians, price per square foot, day counts and budget figures separately, to check the figures on the page. A headless Chromium browser, driven by Playwright, was used to test the page. GitHub Pages publishes the repository through `.github/workflows/pages.yml`.

## Citation

College-town home sales dataset, version 1.0 (2026). University of Illinois-Deloitte Foundation Center for Business Emerging Technologies. Data collected March 2026.

## Who did what

_For teams: replace this line with each member's name and what they did. If you worked alone, delete this section._
