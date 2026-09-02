# Chicago Homicide Geography: A Spatial Analysis

An exploratory spatial analysis examining the geographic distribution of homicides across Chicago neighborhoods over the past decade, with a focus on arrest rate disparities and socioeconomic correlates.

The full analysis, prose and code, is in [`chicago_homicide_analysis.qmd`](chicago_homicide_analysis.qmd) (Quarto). The rendered HTML report is not committed; run `quarto render chicago_homicide_analysis.qmd` to build it.

---

## Overview

This project combines over 8 million crime records from the Chicago Police Department with census tract boundaries and American Community Survey data to investigate:

- **Spatial concentration** — which neighborhoods experience the highest homicide rates
- **Arrest rate disparities** — whether clearance rates vary geographically
- **Socioeconomic drivers** — the relationship between poverty, income, education, and violent crime

The analysis uses geospatial techniques (spatial joins, choropleth mapping) and Census API integration to surface neighborhood-level patterns that inform evidence-based resource allocation.

---

## Key Findings

- **Geographic concentration:** Homicides cluster heavily on Chicago's South and West Sides, with a small number of census tracts accounting for a disproportionate share of incidents
- **Income-crime relationship:** A clear negative correlation exists between median household income and homicide rates at the tract level
- **Arrest rate variation:** Preliminary evidence suggests clearance rates may vary across neighborhoods — a finding that warrants further investigation into resource allocation and community policing dynamics

---

## Project Structure

```
chicago-homicide-analysis/
├── chicago_homicide_analysis.qmd   # Main analysis (Quarto)
├── data/                           # Raw data, not tracked (see "Download the data" below)
│   ├── Crimes_-_2001_to_Present_*.csv
│   └── geo_export_*.{shp,shx,dbf,prj,cpg}
├── .env                            # Census API key, not tracked
├── LICENSE
└── README.md
```

Run `quarto render` to produce `chicago_homicide_analysis.html`.

---

## Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/sys9317/chicago-homicide-analysis.git
cd chicago-homicide-analysis
```

### 2. Download the data

**Crime data:** [Chicago Police Department — Crimes 2001 to Present](https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-Present/ijzp-q8t2)
- Export as CSV and save to `data/Crimes_-_2001_to_Present_YYYYMMDD.csv`

**Census tract boundaries:** [City of Chicago Data Portal — Boundaries - Census Tracts](https://data.cityofchicago.org/Facilities-Geographic-Boundaries/Boundaries-Census-Tracts-2010/5jrd-6zik)
- Export as Shapefile and extract to `data/` (should include `.shp`, `.shx`, `.dbf`, `.prj`)

### 3. Set up Census API access

Get a free API key from [census.gov/developers](https://api.census.gov/data/key_signup.html), then create a `.env` file in the project root:

```
CENSUS_API_KEY=your_key_here
```

### 4. Render the report

```bash
quarto render chicago_homicide_analysis.qmd
```

---

## Tools & Packages

- **Language:** R
- **Report:** Quarto (`.qmd`)
- **Core packages:** 
  - Spatial: `sf`, `tigris`
  - Data wrangling: `tidyverse`, `lubridate`
  - Census data: `tidycensus`, `httr`, `jsonlite`
  - Visualization: `ggplot2`, `scales`

---

## Data Sources

1. **Chicago Police Department** — Crimes 2001 to Present  
   [City of Chicago Data Portal](https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-Present/ijzp-q8t2)

2. **City of Chicago Data Portal** — Census Tract Boundaries (2010)  
   [Boundaries dataset](https://data.cityofchicago.org/Facilities-Geographic-Boundaries/Boundaries-Census-Tracts-2010/5jrd-6zik)

3. **U.S. Census Bureau** — American Community Survey 5-Year Estimates (2019)  
   Variables: Median household income (B19013_001), Bachelor's degree attainment (B29002_007), Poverty count (B29003_002)

---

## Next Steps

- Run multivariate regressions controlling for population density, unemployment, and proximity to transit
- Analyze temporal trends: Has geographic concentration increased or decreased?
- Investigate arrest disparities: Do they correlate with police district budget allocations?
- Link to intervention outcomes: Have violence reduction programs in high-burden neighborhoods shown measurable impact?

---

*By Yosup Shin*
