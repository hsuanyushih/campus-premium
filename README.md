# Campus Premium

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

## Tools we used

Claude Code, an AI coding agent made by Anthropic, wrote and edited the site under the instructions in `AGENTS.md`. The site is plain HTML, CSS and JavaScript, with no framework or build step. Two fonts come from Google Fonts: Source Serif 4 and EB Garamond. Python was used to recompute the medians, price per square foot, day counts and budget figures separately, to check the figures on the page. A headless Chromium browser, driven by Playwright, was used to test the page. GitHub Pages publishes the repository through `.github/workflows/pages.yml`.

## Citation

College-town home sales dataset, version 1.0 (2026). University of Illinois-Deloitte Foundation Center for Business Emerging Technologies. Data collected March 2026.

## Who did what

_For teams: replace this line with each member's name and what they did. If you worked alone, delete this section._
