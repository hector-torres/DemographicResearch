# Product To-Do List

## Project
[ ] Operationalize and document the portfolio, the project, and the product concepts of operations. 

## Features
### Visual Exploratory Data Analysis
User story: as a user, I would like to hover over a targeted geography on a map and see its Census Bureau block group and Texas Leg. Council VTD, 
total population and other key demographic variables (5yr estimate and calculated 1yr estimate), and the number of 
registered voters and other key voting characteristic variables.


- [ ] Merge Texas Leg. Council and Census Bureau geospatial data for mapping and analysis
  - [ ] Identify proper coordinate reference systems for both datasets
  - [ ] Identify correlations between datasets (specifically between Census Bureau block groups and Texas Leg. Council voting tabulation districts)
  - [ ] Create interactive maps to allow for quick visualizations of geography's UCGID and VTD information (using hover text)
  - [ ] For block groups and VTDs that do not fully match, compute geographic percent match (as measured by land area)
- [ ] ID correlated tables between Census Bureau block group and PUMA datasets
- [ ] ID key variables to study for demographic research goal
- [ ] Analyze Census Bureau block group data against PUMA data to calculate estimated demographic shifts in 1yr vs 5yr estimates
  - [ ] Identify block groups within each PUMA area
  - [ ] Develop/identify analytical toolset for calculating shifts

