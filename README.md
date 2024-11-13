# Demographic Research

## Overview
The goal of this project is to use data from various sources in order to gain insights into the demographics of 
targeted geographies. 

Notebooks contained in this project can be categorized as `ETL` notebooks that extract data from source systems and 
load that data into our database, or others those titles reflect their usage. 

The primary notebook here is `geography_and_table_export_selector`, which allows users to select targeted geographies 
and tables from the data available in order to produce files that can be imported into Tableau Public for further 
analysis. 

## Order of Operations
Because of the interconnectedness of some of the datasets being extracted and analyzed, some ETL notebooks (and their 
associated databases loaded) must be run before other notebooks can execute successfully. This section outlines the 
order in which notebooks or ETL scripts must be executed.

### 1. Census Bureau Shapefiles
> **NOTE:  The logic for this ETL notebook is currently part of the Census Bureau ACS Table ETL notebook and will be 
> split out in a future release.**

Code: `ETL/census_bureau_shapefile_ETL.ipynb`
Output: `data/geospatial_files/shapefiles/census_bureau`

Census Bureau shapefiles at the targeted level of analysis are required in order for the ETL process for ACS data at 
that same level of analysis to be properly transformed and loaded into the database. If Shapefiles are not available 
locally then the `census_bureau_shapefiles_ETL` notebook must be run before running 
`census_bureau_acs-<level_of_analysis>_ETL` or any `EDA` notebooks.

### 2. Census Bureau ACS Tables
Code: `ETL/census_bureau_acs_ETL.ipynb`
Output: `data/databases/census_bureau_census_<survey_type>_<survey_year>_<geography_type>.db`

Census Bureau ACS tables represent the core of our data product, and contain data at two levels of analysis (block 
group, and larger than block group) across two surveys (ACS Supplemental Estimate 1-year estimates and ACS 5-year 
estimates), totalling approximately 60 tables for non-block group geographies and around 1100 tables for block group 
geographies.

### 3. Census Bureau Crosswalks
Code: `ETL/census_bureau_acs_table_crosswalk_etl.ipynb`
Output: `data/databases/census_bureau_census_acs-acsse_crosswalk.db`

This notebook extracts the common tables from Census Bureau ACS Supplemental Estimates 1-year data and ACS 5-year data
so that we can have common reference points of analysis across both time and space. 

### 4. Texas Secratary of State Voter Data File
Code: `ETL/tx_sec_of_state_voter_data_file_ETL.ipynb`
Output: `data/databases/texas_secretary_of_state/voter_data_file.db`

This notebook extracts voter data from Texas Secretary of State fixed width delimited file in order to begin analysis of 
individual voter patterns.

#### 4.1. Address Geocoding
Code: `ETL/address_geocode_ETL.ipynb`
Output: `data/databases/texas_secretary_of_state/voter_data_file.db`

Once the database is loaded, it is run against the address geocoding notebook so as to be able to conduct geospatial 
analysis on individual voter data. 

## Datasets Awaiting Future Workflows

### 1. Texas Legislative Council Comprehensive Election Datasets
Code: `ETL/tx_leg_council_comprehensive_election_dataset_ETL.ipynb`
Output: `data/datasets/texas_legislative_council`

This will extract data from the Texas Legislative Council, the research arm of the Texas Legislature, from their FTP 
servers as comma-separated value files for all elections available. There are no deltas available (as of October 2024), 
so full datasets must be downloaded after every election.

### 2. Texas Legislative Council Comprehensive Election Datasets
Code: `ETL/tx_leg_council_comprehensive_election_dataset_ETL.ipynb`
Output: `data/databases/texas_legislative_council/texas_legislative_council_election_dataset_2022.db`

In order to normalize and organize TLC data, this notebook creates a database table for every new entry in the TLC data 
extracts - this keeps a historical record of their data if they ever change availability or content of previous year 
data.

### 3. Texas Legislative Council Voting Tabulation District Shapefiles
Code: TBD (manual process as of October 2024)
Output: `data/geospatial_files/shapefiles/texas_legislative_council/<analysis_year>/VTDs_<analysis_short_year><election_type>.[shp, dbf, shx]`

## Notes
ACS Release Schedule
- https://www.census.gov/programs-surveys/acs/news/data-releases/2023/release-schedule.html


## Sources
- Census Bureau TIGER/Line Shapefiles (FTP site)
    - https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html
- Census Bureau datasets (API)
    - https://api.census.gov/data.html 
- Texas Legislative Council Comprehensive Election Datasets (FTP site)
  - https://data.capitol.texas.gov/dataset/comprehensive-election-datasets-compressed-format
- Texas Legislative Council Voting Tabulation Distrcits (FTP site)
  - https://data.capitol.texas.gov/dataset/...
- Texas Secretary of State Voter Registration Information Request (printable PDF to be submitted to Secretary of State office)
  - https://www.sos.state.tx.us/elections/forms/pi.pdf

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
- US Election Assistance Commission Availability of State Voter Files
  - https://www.eac.gov/sites/default/files/voters/Available_Voter_File_Information.pdf