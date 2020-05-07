# US City COVID-19 ZIP Code Analysis

This repository contains data and code supporting a BuzzFeed News article about city-level ZIP code demographics and COVID-19 cases, published May 7, 2020. See below for details.

## Data

### ZIP code–level data

The analysis uses ZIP–code level case counts (as of May 4, 2020 for each city except for Detroit, which is as of May 7, 2020) for the following five cities, stored in the `data/raw` directory:

- New York City, [sourced from the the city's Department of Health](https://github.com/nychealth/coronavirus-data)
- Chicago, [sourced from Illinois Department of Health](https://www.dph.illinois.gov/covid19/covid19-statistics)
- Detroit, [sourced from the city's COVID-19 ZIP code dashboard](https://codtableau.detroitmi.gov/t/DHD/views/NEWDASHBOARDPublicCOVIDTableau/ZipCodeDash?%3AisGuestRedirectFromVizportal=y&%3Aembed=y)
- Philadelphia, [sourced from the Pennsylvania Department of Health](https://www.health.pa.gov/topics/disease/coronavirus/Pages/Coronavirus.aspx)
- Baltimore, [sourced from the Maryland Department of Health](https://coronavirus.maryland.gov)

### City ZIP shapefiles

The `data/raw` directory also includes ZIP-code level shapefiles for each of the five cities. Those geospatial files come from each city's open data portals and are used to filter for the appropriate ZIP codes and create the maps that are included in the article.

### Census data

The [demographic data](data/processed/census/zip_census_data.csv) used in the analysis comes from the 5-year ACS estimates for 2018 at the ZCTA level. The data file included in this repository has been pre-processed from seven different data files that are not included here, in order to reduce the size of the raw data in this repository.

### CBSA and county data

The [`data/county-data`](data/county-data) directory contains several datasets relevant to the metro-area calculations described below. The datasets are:

- `cbsa.csv`, which lists all Census-defined [Core-based statistical areas (CBSAs)](https://www.census.gov/topics/housing/housing-patterns/about/core-based-statistical-areas.html): their titles, numeric codes, and [populations](https://www.census.gov/data/developers/data-sets/popest-popproj/popest.html).

- `cbsa-counties.csv`, which lists all counties in each CBSA, via the Census' ["delineation" files](https://www.census.gov/geographies/reference-files/time-series/demo/metro-micro/delineation-files.html) (Sept. 2018 vintage).

- `nyt-county-counts.csv`, which contains [the New York Times' tabulations](https://github.com/nytimes/covid-19-data/) of county-level COVID-19 case and death counts, through May 4, 2020.


## Analysis

### Analyze ZIP code–level COVID-19 case / demographic correlations

The [`city-demographic-factors-analysis.ipynb`](notebooks/city-demographic-factors-analysis.ipynb) notebook loads the data for each city, calculates correlations between various demographic factors and per capita case counts (at a ZIP code level), and graphically explores some of those correlations. It also outputs the GeoJSON and CSV files used to create the maps and scatterplots in the story.

### Calculate population, cases, and deaths in largest US metro areas

The [`calculate-metro-area-proportions.ipynb`](notebooks/calculate-metro-area-proportions.ipynb) notebook uses the county-level data described above to calculate the proportion of population, COVID-19 cases, and COVID-19 deaths in the United States' 15 largest metro areas, relative to US totals.

## Licensing

All code in this repository is available under the [MIT License](https://opensource.org/licenses/MIT). Files in the output/ directory are available under the [Creative Commons Attribution 4.0 International (CC BY 4.0) license](https://creativecommons.org/licenses/by/4.0/).

## Contact

If you have any questions about this repository you can reach out to John Templon at [john.templon@buzzfeed.com](mailto:john.templon@buzzfeed.com).

Looking for more from BuzzFeed News? [Click here for a list of our open-sourced projects, data, and code.](https://github.com/BuzzFeedNews/everything)
