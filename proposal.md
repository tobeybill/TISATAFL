# Research Proposal: Does CEO Treatment Affect Shareholder Confidence?
### *There is Such a Thing as Free Lunch*
---

### Research Question

Through this project we plan on analyzing data on CEO treatment and how it affects the shareholder confidence in the companies these executives lead. The treatment metrics we will be focused on are 1) CEO compensation 2) forced CEO turnover and 3) Other factors not yet discovered. To measure shareholder confidence, we will look at the company’s stock price performance in a given year and/or after a given turnover date. We will also conduct a dismissal event study in order to possibly uncover any correlation with firm performance and CEO dismissal (unexpected or not). 

***The specific question*** we are trying to answer is: *Is there a relationship present between the compensation and/or forced turnover of a CEO and the stock price of the companies they lead?*

### Methodology

In order to help us have a more defined analysis and conculsion, here are some papers that we are going to keep in mind as we go forward. 
- https://www.sciencedirect.com/science/article/pii/S0929119905000738?casa_token=GzFuxTXx364AAAAA:rBG1N7rQAqyJXOadR93Q-naHqKBa9PZZBb9RZxvgScRJcAdlMFKfxZp-LGvmz_Z--Pgz32SkUmI
  - This one makes a comment on finding that "...excess compensation (both director and CEO) is associated with firm underperformance."
  - This paper helps us understand that their are other complexities in the pay strucuture that might have ab effect on firm performance.
  - This proposal uses Cash and Total Compensation as the dependant variables of the study, firm charactersitics are lagged by one year.
- https://www.clutejournals.com/index.php/JBER/article/view/2357
  - Expects there is a direct correlation
  - Uses company revenue, year-to-year change in net income, and year-to-year change in total shareholder return for company charateristics.
  - Looking into proxy statements may help us understand the naunces of CEO compensation.
  - The used 6 variables to measure comp: Base Salary, Cash Bonus, Perks/Other, Stock Awards, Option Awards, and Total Compensation.
- https://papers.ssrn.com/sol3/papers.cfm?abstract_id=1752563
  - This one digs into the background of a CEO and how that affects their performance
  - "Results show a select group of schools educate a large proportion of top CEOs."
  - University rank is based on how many graduates are CEO's
  - FORBES publishes a list of ~500 CEO's every year. The list includes company metrics, CEO compensation, and CEO background information.
We will start with these to start our research and what variables we should take into account. Different backgrounds may possible require different treatment than others. Definitely something we could dig into if there is any data of interest. 

OLD - ***We hypothesize*** that both high compensation and forced turnovers will be positively correlated with a company’s stock price, as higher compensation is usually a result of company overperformance and a forced turnover usually occurs with problematic CEOs.

***We hypothesize*** that CEO compensation has a statistically significant correlation to the firms performance in terms of Stock Price. Where CEO's with higher compensatio overperform, and the company performs poorly leading up to a forced turnover.
compensated CEO's 


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

***Data we have currently*** includes information on [CEO compensation](https://wrds-www.wharton.upenn.edu/pages/get-data/compustat-capital-iq-standard-poors/compustat/execucomp/annual-compensation/) 2010-2019 and [forced CEO turnovers](https://wrds-www.wharton.upenn.edu/pages/get-data/contributed-data-forms/forced-ceo-turnover/) that occurred during that time period. In order to keep in mind how the market reacts to CEO dismissals, we will also include data from this [set](https://wrds-www.wharton.upenn.edu/pages/get-data/event-study-wrds/). We will try all dismissals and repeat for the subsamples, for example we could look at declining/rising of sales when there are dismissals (surprises or expected). 

We will ***collect more data*** by further utilizing the data sources available to us to find additional data on CEOs. Additionally, we will need to collect stock price data from Yahoo Finance and find more data on other factors we hope to consider, such as industry or geography.

***Raw inputs*** currently include .csv files we will store in an inputs folder in our repository.

We will transform the raw data through the following preliminary steps:
- Merge over the company gvkey (which is present in both datasets)
- Determine which executives in the compensation dataset are CEOs (based on the column with position data)
- Pull stock data from yahoo finance around relevant dates and years measured
- Calculate returns utilizing methods learned in class
- Perform data visualization

Once transformed, we will analyze the data using statistical techniques such as regression analysis, correlation analysis, and descriptive statistics to identify potential correlations between CEO treatment and company stock success. We will also conduct subgroup analyses based on different factors such as CEO age, company industry, etc. 








***LAST PART FROM BOWEN
Examining the link between pay and firm value is complicated. It's an equilibrium outcome in a fragmented and unique labor market. The economics of how incentives need to be designed are continually being revised and adjusted, and this process creates links between firm size and pay. CEOs
Your "specific question" reads like comp --> firm perf --> value
Your "hypo" reads like firm perf --> comp
In your revision, add a section called "Methodology" and list some papers from the lit review above and add snippets about how they might help you set up your test about CEO pay and firm value.
