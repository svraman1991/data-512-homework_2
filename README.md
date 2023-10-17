# Ramans repository for Data 512 Assignments - Au23 - Assignment 2

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

TO BE NOTED: the input state file doesn't have data for the states of Nebraska and Connecticut. 

## Final Output files:
The final output is in the folders: "Output Files". This file contains the article quality prediction and 2022 Estimated population for the cities by state and regional division.
The fields in this file are as below:

Fields:
state (string): The US state
page_title (string) : the page title for the Wiki article of the city
regional_division (string): The region and division for the city
Population Est. 2022 (numeric): 2022 estimated population for the state.
lastrevid (numeric) : The ID column used by Wiki to fetch articles details by
prediction (string) : the predicted article quality as obtained from the ORES API
probability (numeric) : the probability for the associated article quality as obtained from the ORES API
prediction_text (string) : user-friendly description of article quality

## Code files
Present in the folder "Notebooks"
1) Raman_Data_512_HW2_final.ipynb - this notebook contains all the code and commentary for this analysis
   
2) wp_ores_liftwing_example.ipynb - this code example was developed by Dr. David W. McDonald for use in DATA 512 and is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.0 - August 15, 2023

3) wp_page_info_example.ipynb - this code example was developed by Dr. David W. McDonald for use in DATA 512 and is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.0 - August 15, 2023
   
## Research Implications:

The primary code block on this project was to access Wikipedia to obtain page information for the cities and then predict the article quality for the same using ORES model.
However, given the size of the data, it is pertinent to plan the process to access the API data.
We have to keep in mind constraints such as timeouts or even vulnerabilities as we could have our accounts blocked or monitored for extreme activity.
Multiple API calls by people working on the same project (especially near the deadline) could resemble a type of DOS attack as we flood the server with requests, all from accounts that were newly created. 

One of the ways to use such resources, especially from a free source, would be to be understanding of the quality for others.
To this extent, we can introduce methods such as adding breaks and spreading the activity over a few days instead of an all nighter. 
Further, indexing the code and feeding in chunks of data to get API details would make sense as this helps us keep track of the requests and resume activity based on the index of the record we encountered errors at.

Timeout issues were more frequent for the ORES model score prediction and to this extent, serializing the data and loading it in chunks seems to be the optimal approach.
Further, error handling is necessary as we might still get responses from the server, but the responses could be error codes as opposed to the requested data.

In terms of the data itself, I assumed that the states with the largest population centers would have more higher quality articles and that number of articles per capita might not be the most optimal KPI here.
The reason for this being that the articles are by city and not by population. This is akin to senate representation where each state gets 2 representatives irrespective of the population.

Once the data was obtained, it was obvious that the most populous cities need not have the highest quality of articles per capita or outright.
In hindsight, this seems obvious as larger cities tend to have more participation which could lead to debates or articles being locked as a lot of the segments could be colored by psychological aspects such as political leanings. This is indeed true for cities such as Seattle and San Francisco, which are de-facto tech hubs in the US. However, their articles are only considered B-class and are even locked for editing at certain periods. 
And on the other end, Seattle suburbs such as Everett and Lynnwood are featured articles! 

Bias in participation need not imply bias in quality and for a site such as Wiki, that is often plagued by the lack of verified moderators, it would explain this dissonance.

Apart from the above, here are some responses to a set of questions on this data and analysis:

1) What biases did you expect to find in the data (before you started working with it), and why?
   a) As mentioned above, I expected big cities and tech hubs to have a higher proportion of good quality articles as opposed to more interior cities. This was based on the assumption that more people are technologically inclined at such places and would take greater efforts to add details to the place they are a domicile of. However, that has not really been the case and the efforts of the committed few often outweigh the headaches associated with moderating and ascertaining the sources from a myriad of accounts

2) What might your results suggest about (English) Wikipedia as a data source?
  a) In spite of the biases and vagaries of the API calls and results, I believe that Wikipedia is a very valid source for initial analysis and as square one to start one's research. With the increasing trend of companies locking up their data from API access, Wiki might well be one of the last bastions of publicly available and near-verified data sources. Analysis is in the hands of the data scientist. One could run with "results" that enforce their bias or preconceived notions or use the data to report findings. In that sense, Wiki is still a great source to obtain data from and reach high level analysis goals. Another point to be noted is the completeness of data, for instance, the state list in my input did not have details for the states of Nebraska and Connecticut, hence it is vital to be cognizant of the limitations of these results especially at a division or region level. 

3) How might a researcher supplement or transform this dataset to potentially correct for the limitations/biases you observed?
  a) Be it Wikipedia or other sources, unless there is a universally accepted single source of truth, it would be detrimental to rely on one source. This can be accounted for by going through the articles that are used to create the content for this site. Similarly, using government data sources and renowned news publication would add not just dimensions but a more unbiased source to the research. If more time were devoted to data requisition (provenance) over training models, that is to say, if we trained ourselves to learn the data before running it through machine learning, not only will our results be rich, but we can avoid controversies and human errors. After all, stats without context is not much different from a grand lie with a kernel of truth to it.

