# data-512-homework_1
# Professionalism & Reproducibility
## Homework #1
The goal of this assignment is to construct, analyze, and publish a dataset of monthly article traffic for a select set of pages from English Wikipedia from July 1, 2015 through September 30, 2024.

## Data Source License
- **License:**[Wikimedia Terms of use](https://www.mediawiki.org/wiki/API:REST_API#Terms_and_conditions) 

## API
The data for this project is sourced from the Wikimedia API, which provides access to a wide range of information related to Wikipedia articles and their pageviews. Specifically, we use the "pageviews" endpoint of the Wikimedia API to retrieve pageviews data for a selected list of Wikipedia articles.

- **WIKI API Endpoint:** [Wikimedia Pageviews API](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews)
- **Python requests module:** [Python requests module](https://pypi.org/project/requests/)

## Data Files
### Input file:
- **rare-disease_cleaned.AUG.2024**: This contains the full list of titles of diseases whose data is being pulled out of wikimedia API.

### Outputs:

The json files are generated after fetching the API response from the Wikimedia for each disease. Each disease is a dictonary key and the value is a list of dictinaries containing the details such as: project, article, granularity, timestamp, agent, views

- **rare-disease_monthly_cumulative_201507-202409**
- **rare-disease_monthly_desktop_201507-202409**
- **rare-disease_monthly_mobile_201507-202409**

### Analysis and Visualization Outputs:

The generated plots are stored in the folder Analysis_plots.

- **MaximumMinimumAverage.png**: This image shows the plot of monthly page views of the most and least viewed articles accessed through desktop and mobile.
- **Top10PeakPageViews.png**: This image shows the plot of the monthly page views of the top 10 articles with the highest peak monthly views.
- **FewestMonths.png**: This is a plot showing the monthly page views of the top 10 articles with the fewest months of data available.

## Running the code
Download the python notebook and click on run all cells to run the code. The duration to run the notebook can take between 45 minutes to 1.5hrs based on the laptop and gpu support used. 



## Known Issues and Considerations
1. The Date range to pull the data has to specified in `ARTICLE_PAGEVIEWS_PARAMS_TEMPLATE`. This is not dynamic.  
2. The data collection process is time consuming and can face issues such as timeout or lost connections. Re run the code using a different platform or increase the processing power in your system.  
3. Rate Limiting and Throttling has to be kept in mind to avoid being temporarily blocked.  
4. Some articles may have missing data for certain months due to API limitations or data availability issues.  
5. The data acquisition code taken from Dr. David's work failed to encode the `/` in article titles like "Sulfadoxine/pyrimethamine".   
    `urllib.parse.quote(request_template['article'].replace(' ', '_'))`   
    was replaced with   
    `urllib.parse.quote(request_template['article'].replace(' ','_'), safe='')`    
    The safe parameter encodes the "/" character.  
    



