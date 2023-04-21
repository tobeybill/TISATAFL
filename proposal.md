# Research Proposal: Does CEO Treatment Affect Shareholder Confidence?
### *There is Such a Thing as Free Lunch*
---

### Research Question

Through this project we plan on analyzing data on CEO treatment and how it affects the shareholder confidence in the companies these executives lead. The treatment metrics we will be focused on are 1) CEO compensation 2) forced CEO turnover and 3) Other factors not yet discovered. To measure shareholder confidence, we will look at the company’s stock price performance in a given year and/or after a given turnover date. 

***The specific question*** we are trying to answer is: *Is there a relationship present between the compensation and/or forced turnover of a CEO and the stock price of the companies they lead?*

***Academic Journals to keep in mind***


***We hypothesize*** that both high compensation and forced turnovers will be positively correlated with a company’s stock price, as higher compensation is usually a result of company overperformance and a forced turnover usually occurs with problematic CEOs.

---
### Necessary Data

Our final dataset needs to contain the following:
- Observation of [Firm, Year]
  - Firm ticker
  - Year
- CEO name during that year
- Firm industry
- If the CEO was forced out
  - Date of announcement
  - Returns following announcement
- CEO compensation in year
- Returns during that year
The sample period is 2010-2019, we plan on restricting it to this date range due to availability of data.

***Data we have currently*** includes information on [CEO compensation](https://wrds-www.wharton.upenn.edu/pages/get-data/compustat-capital-iq-standard-poors/compustat/execucomp/annual-compensation/) 2010-2019 and [forced CEO turnovers](https://wrds-www.wharton.upenn.edu/pages/get-data/contributed-data-forms/forced-ceo-turnover/) that occurred during that time period.

We will ***collect more data*** by further utilizing the data sources available to us to find additional data on CEOs. Additionally, we will need to collect stock price data from Yahoo Finance and find more data on other factors we hope to consider, such as industry or geography.

***Raw inputs*** currently include .csv files we will store in an inputs folder in our repository.

We will transform the raw data through the following preliminary steps:
- Merge over the company gvkey (which is present in both datasets)
- Determine which executives in the compensation dataset are CEOs (based on the column with position data)
- Pull stock data from yahoo finance around relevant dates and years measured
- Calculate returns utilizing methods learned in class
- Perform data visualization

Once transformed, we will analyze the data using statistical techniques such as regression analysis, correlation analysis, and descriptive statistics to identify potential correlations between CEO treatment and company stock success. We will also conduct subgroup analyses based on different factors such as CEO age, company industry, etc. 
