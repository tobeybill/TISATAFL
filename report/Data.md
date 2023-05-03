# Data and Variables

## Data

All of our data was extracted from WRDS. All data regarding director and CEO compensation and demographics came from Execucomp. Firm accounting variables and other firm specific information came from Compustat. All stock prices were pulled from CRSP.

We cross referenced multiple studies to find determinants of CEO and director compensation as well as firm performance. Our sample size comprised of firms in the S&P500 from 2010 - 2019. We chose 2010-2019 to avoid the corporate scandals of the early 2000's and the impact of COVID on the market.

### BOD Compensation and Determinants
Director compensation was derived as their total compensation including cash, value of stock options and option awards, non-equity incentive plan compensation, change in pension value and nonqualified deferred compensation earnings, and all other compensation.

We used accounting based firm valuations and market performance as determinants for predicting Board of Directors
compensation. The accounting variables and compensation variables (not including total compensation)are lagged 
one year, because we are assuming that current total compensation is impacted by previous years performance. The 
accounting metrics of a firm are resilient to equity market changes. These metrics focus on internal firm performance, which will reduce the impact a strong market position will have on predicted compensation. A strong market artificially inflates firm values, even if the firm is not doing well internally. We included market performance determinants in our analysis because BOD packages usually contain some equity incentive (Dah and Frye).

### CEO Compensation and Determinants
The CEO variables where also lagged by one year not including total compensation, we determined past compensation can be used as an indicator for future comp. CEO determinants are a combination of created variables and stock awards. We created an Ownership Ratio, Ownership Power, Year Served, and Prestige determinants. The Ownership Ratio is the CEO Stock Awards divided by BOD Stock Awards. This variables represent the equity power a CEO holds over a Board of Directors. If a CEO holds more equity than the board, then they hold more power over the company and have a greater influence on the board. We then created a determinant called Ownership Power. This is a binary categorical variable. This variable indicated whether the CEO Ownership Ratio was above the CEO Ownership Ratio median. We predict that CEO's with a higher ownership ratio will have more control over the firm and thus more influence on their pay. For Years Served, we took the difference between the year the CEO was on-boarded and the recorded year. CEO's that serve longer terms are more experienced and are more likely to receive higher pay. We based Prestige Power off of Years Served. Prestige power is a binary categorical variable that indicates whether time served is above the median. This implies a CEO can gain prestige power during their term (Bouteska and Mefteh-Wali)

### Determinants of Firm Performance
The review written by Sigo explores a wide variety of contributing factors to firm performance: profitability 
performance, growth performance, market value performance of the firm, customer satisfaction, employee 
satisfaction, environmental audit performance, corporate governance performance and social performance. Although 
this may seem exhaustive, the paper did not actually test any of these variables as controls. For our analysis, 
we focused on the profitability performance, growth performance, and market value performance due to their 
availability in the compustat dataset. All of these determinants are later used to predict firm performance.

### Exploratory Data Analysis
After querying the data from WRDS, we did an Exploratory Data Analysis or EDA on our data frames. Our EDA leads us to dropping variables deemed unnecessary in our analysis, imputing data into missing or NaN data fields, and creating new variable identifiers. 

The data sets that were queried from WRDS where very extensive. We did not have use for all of the variables in the data sets, and selected the ones we determined to be pertinent to our project based on the literature we read. We renamed variables to have more comprehensive labels. For missing data we imputed values depending on the 
variable case. For the variables we did not create, we imputed missing values with that variables mean. The imputed means where done according to market value bins. For Example, the Tiny firms would not be imputed with the Large firms means. We had to normalize the variables we created. Some of the division resulted in NaN and 'inf' values. We understood that the NaN results came from dividing zero and 'inf' was the result of dividing by zero. We imputed the NaN results with zero and capped the 'inf' results to the maximum value of that variable set. 

Out of the two CEO total compensation values, we kept the variable that used the Black Scholes Model to value the options held by the CEO. (TDC1) 



-----------


## Variables


### Director Compensation Variables

__Dependent Variables (Test Set)__
- Total Director Compensation


__Independent Variables (Train Set)__
__Numeric Data - Part of the BOD compensation package and Firm performance__
- Other Compensation
    - All other non traditional compensations
- Non Equity Incentives
    - Incentives plan that does not include equity
- Cash Fees
    - Fees earned or paid to the BOD
- Stock Awards
    - Company Stock awards to the BOD
- Option Awards
    - Value of the option awards given to the BOD
- Total Other Compensation
    - As reported in SEC filings
- Total Non Equity Incentives
    - As reported in SEC filings
- Total Cash Fees
    - As reported in SEC filings
- Total Stock Awards
    - As reported in SEC filings
- Total Option Awards
    - As reported in SEC filings
- Market Value of the Firm
    - The market value of the firm
- Total Fiscal Market Value
    - Market book value of the firm
- Liquidity (Quick Ratio)
    - Firm liquidity
    - Current Assets / Current liabilities
- Net Income
    - The Net Income of the firm
- Number of Employees
    - How many employees are at the firm
- Debt to Equity Ratio
    - Total firm debt / total Shareholder Equity
    - Company financial leverage
- Assets in Place
    - Value of property the firm has invested in
- Capex by Assets
    - How much the firm has invested in itself
- Return on Equity
    - Net Income / Shareholder equity
    - How efficiently the firm uses equity investments
 
__Categorical data__
- Size Category
    - Determined by market value of the firm
-----------

### CEO Compensation Variables
__Dependent Variables (Test Set)__
- Total CEO Compensation

__Independent Variables (Train Set)__
**Created Variables**
- Ownership Ratio
      - CEO Stock Awards / BOD Stock Awards
      - If the ratio is 'inf' (BOD Stock Awards = 0) we replaced it with the highest ratio (406.17953)
          - If the ratio is 'NaN' (CEO Stock Awards = 0) we replaced it with zero
- Ownership Power
      - 1 if the Ownership Ratio is above the median of the data set 0 otherwise
      - We used the median to avoid outliers in the ratio overly impacting our analysis
- Years Served
      - This is the amount of time the CEO served at the firm 
- Prestige Power
       - 1 if the Year Served is above the median of the data set 0 otherwise
       - We used the median to avoid outliers in the ratio overly impacting our analysis


**Numeric Data**
- CEO Age
     - How old the CEO was during that year
- Stock Awards
    - Value of the stock awards given to the CEO
- Market Value
    - Market value of the firm


**Categorical data**
- Size Category
   - Determined by market value of the firm
-----------

### Firm Performance Variables

__Dependent Variables (Test Set)__
- TobinsQ

__Independent Variables (Train Set)__
- Return on Assets
- EBITDA Margin
- Net Income / Revenue
- Return on Equity
- Earnings per share
- Change in stock price
- Dividend yield
- Volatility
- Market value added
- Asset growth
- Total revenue growth
- Net income growth
- Employee growth

