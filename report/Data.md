# Data and Variables

We pulled our data from the WRDS Compustat, Execucomp, and CRSP databases.

-----------
## Director Compensation Variables
### Dependent Variables (Test Set)
- Total Director Compensation
### Independent Variables (Train Set)
#### Numeric Data - Part of the BOD compensation package
These variables are industry standard for calculating Board of Director compensation and Firm performance.
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
#### Categorical data
- Size Category
    - Determined by market value of the firm
-----------
## CEO Compensation Variables
### Dependent Variables (Test Set)
- Total CEO Compensation
### Independent Variables (Train Set)
### Created Variables
- Ownership Ratio
      - CEO Stock Awards / BOD Stock Awards
      - If the ratio is 'inf' (BOD Stock Awards = 0) we replaced it with the highest ratio (406.17953)
          - If the ratio is 'NaN' (CEO Stock Awards = 0) we replaced it with zero
- Ownership Power
      - 1 if the Ownership Ratio is above the median of the data set 0 otherwise
      - We used the median to avoid outliers in the ratio overly impacting our analysis
- Years Served
      - This is the amount of time someone served as CEO for a firm 
- Prestige Power
       - 1 if the Year Served is above the median of the data set 0 otherwise
       - We used the median to avoid outliers in the ratio overly impacting our analysis
#### Numeric Data
- CEO Age
     - How old the CEO was during that year
- Stock Awards
    - Value of the stock awards given to the CEO
- Market Value
    - Market value of the firm
#### Categorical data
- Size Category
   - Determined by market value of the firm