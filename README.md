# UK Asset Allocation Analyser

A Python-based asset allocation system built on a master universe of 2,400+ LSE-listed securities. The project automates the classification of ETFs, ETCs and UK stocks by asset class and geography, then analyses client portfolio allocations using live market prices.

## Project Structure

This project is split into two parts:

### Part 1 — Master Securities Universe (Asset Allocation Cleaning.ipynb)
- Loads the full LSE ETF/ETP securities list (2,300+ instruments)
- Merges with FTSE 100 constituents
- Automatically categorises every security by Asset Class and Geography using keyword classification logic
- Outputs a clean master reference file: `master_securities.csv`

**Asset Classes:** UK Equity, Global Equity, Fixed Income, Alternatives, Cash

**Geographies:** UK, US, Europe, Japan, Asia Pacific, Emerging Markets, China, Global

### Part 2 — Asset Allocation Analyser (asset_allocation_analyser.ipynb)
- Reads a client holdings CSV (`client_holdings.csv`)
- Pulls live prices via yfinance for each holding
- Calculates £ value and portfolio weighting per holding
- Looks up each security in the master universe
- Outputs full asset class and geographic allocation per client
- Supports multiple clients in a single run
- Exports results to CSV for Power BI dashboard

## Data Sources
- LSE ETF/ETP securities list: [London Stock Exchange](https://docs.londonstockexchange.com/sites/default/files/documents/list_of_etfs_and_etps_securities_6.xls) — download and place in project folder before running Part 1
- FTSE 100 constituents: sourced via GitHub (yfiua/index-constituents)
- Live prices: Yahoo Finance via yfinance

## How To Run

**Part 1 — Build the master universe:**
1. Download the LSE ETF list from the link above
2. Place it in your project folder
3. Run `Asset Allocation Cleaning.ipynb` top to bottom
4. This generates `master_securities.csv`

**Part 2 — Run the analyser:**
1. Populate `client_holdings.csv` with your client portfolios
2. Run `asset_allocation_analyser.ipynb` top to bottom
3. Results print to screen and save to `powerbi_feed.csv`

## Input Format

`client_holdings.csv` should follow this structure:

| Client | Risk_Profile | Ticker | Shares |
|--------|-------------|--------|--------|
| John Smith | Balanced | VWRL.L | 150 |
| John Smith | Balanced | SHEL.L | 100 |
| Jane Doe | Cautious | IGLT.L | 500 |

## Output Example
