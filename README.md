# Demographics Research

## Overview
The goal of this project is to use data from various sources in order to gain insights into the demographics of 
targeted geographies. 

Notebooks contained in this project can be categorized as `ETL` notebooks that extract data from source systems and 
load that data into our database, or as `EDA` notebooks that use database data to produce analyses. 

## Requirements
Census Bureau Shapefiles are required in order for the ETL process for ACS data to be properly transformed and loaded 
into the database. If Shapefiles are not available locally then the `census_bureau_shapefiles_ETL` notebook must be run 
before running `census_bureau_acs-<level_of_analysis>_ETL`, `cartographer`, or any `EDA` notebooks.

## Notes
ACS Release Schedule
- https://www.census.gov/programs-surveys/acs/news/data-releases/2023/release-schedule.html


## Sources
- Census Bureau TIGER/Line Shapefiles
    - https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html
- Census Bureau datasets available via API
    - https://api.census.gov/data.html 

## References
- American National Standards Institute (ANSI), Federal Information Processing Series (FIPS), and Other Standardized 
Geographic Codes
    - https://www.census.gov/library/reference/code-lists/ansi.2010.html 
- Census Decennial Maps Directory
    - https://www2.census.gov/geo/maps/DC2020/
- Mapping Guide
    - https://medium.com/@jl_ruiz/plot-maps-from-the-us-census-bureau-using-geopandas-and-contextily-in-python-df787647ef77
- ACS Release Schedule
    - https://www.census.gov/programs-surveys/acs/news/data-releases/2023/release-schedule.html
- Understanding ACS Single- and Multi-Year Estimates
  - https://www.census.gov/content/dam/Census/library/publications/2018/acs/acs_general_handbook_2018_ch03.pdf