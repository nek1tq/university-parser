# US News Best Global Universities Parser

Python script that scrapes statistical data from 2,551 universities listed on [US News Best Global Universities Rankings](https://www.usnews.com/education/best-global-universities/rankings) and exports it to Excel.

## What it does

1. Fetches the full list of universities via the US News search API
2. Visits each university page and extracts key metrics from HTML
3. Saves results to Excel with the following columns:
   - University Name
   - Total number of students
   - Link to university page
   - Number of international students
   - Total number of academic staff
   - Number of international staff
   - Number of undergraduate degrees awarded
   - Number of master's degrees awarded
   - Number of doctoral degrees awarded
   - Number of research only staff
   - Number of new undergraduate students
   - Number of new master's students
   - Number of new doctoral students

## Features

- **Resume support**: saves progress to `progress.json`, so if interrupted it continues from where it left off
- **Auto-retry**: retries failed requests once after a 5-second delay
- **Incremental Excel export**: saves Excel every 10 universities

## Tech stack

- Python 3
- `requests` — HTTP requests
- `openpyxl` — Excel export
- `re` + `html` — HTML parsing (no heavy dependencies like BeautifulSoup needed)

## Usage

```bash
pip install requests openpyxl
python parser.py
```

Output: `US_News_2025-2026.xlsx`

## Notes

- Some universities (~1,900 out of 2,551) don't publish detailed statistics on US News — these will have empty cells
- Top ~600 universities typically have full data (11/11 metrics)
- Requires VPN if accessing from restricted regions
