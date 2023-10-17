# Data512_UW_RS

Ramans repository for Data 512 Assignments - Au23 - Assignment 2

## Goal:
  a) Understand data retrieval from Wiki pages and use the data to predict article quality
  b) Apply ORES machine learning model to get the article quality for Wikipedia pages
  c) Understand the biases and inferences from the number of articles and article quality at a state level (for US states) and per capita level
  d) Understand reproducibility and methods to use pre existing code or packages to create ones' own work

## Licenses:
The analysis here uses data from Wikipedia and its use is covered under - 
Wikimedia Terms of use: https://www.mediawiki.org/wiki/API:REST_API#Terms_and_conditions

Further, for the API's used, the documentation for their usage can be found at - 

MediaWiki Action API: https://www.mediawiki.org/wiki/API:Main_page
ORES API: https://www.mediawiki.org/wiki/ORES

Overall, this work (including code and the data) is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.1 - August 14, 2023

## Input files:
These files are present in the "Input Files" folder of this repo and it contains the list of cities by US States that were used for the analysis in this project

1) us_cities_by_state_SEPT.2023.xlsx - list of states and their cities with Wikipedia articles, current as of 16-Oct-2023
2) US States by Region - US Census Bureau.xlsx - the division and region information for the states
3) NST-EST2022-POP.xlsx - the 2022 population estimates for US States and regions, the population estimates are obtained from this link [State Population Totals and Components of Change: 2020-2022](https://www.census.gov/data/tables/time-series/demo/popest/2020s-state-total.html)


## Intermediate Data files:

As part of the code, CSV files of the data pulled were created, these are present under the CSV_Files folder: 
1) Desktop_Page_Views.csv: This file has the output of the data pull for the desktop views of the movie list
   
2) Mobile_App_Page_Views.csv: This file has the output of the data pull for the mobile app views of the movie list

3) Mobile_Web_Page_Views.csv: This file has the output of the data pull for the mobile web views of the movie list

## Final Output files:
The final output is in the folders: "". 

File: 
Fields:
state (character): state of the article.
regional_division (character): regional division of the article.
population (integer): 2022 population of the state.
article_title (character): title of the article.
revision_id (integer): last revision ID of the article obtained from MediaWii Action API.
article_quality (character): predicted article quality obtained from the ORES API.



## Code files
Present in the folder "Notebooks"
1) Raman_Data_512_HW2_final.ipynb - this notebook contains all the code and commentary for this analysis
   
2) wp_ores_liftwing_example.ipynb - this code example was developed by Dr. David W. McDonald for use in DATA 512 and is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.0 - August 15, 2023

3) wp_page_info_example.ipynb - this code example was developed by Dr. David W. McDonald for use in DATA 512 and is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.0 - August 15, 2023
   
## Research Implications:
