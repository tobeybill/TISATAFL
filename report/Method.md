## The Process:

Prior literature has individually examined the impact of Director compensation and CEO compensation on firm performance, but there are less studies that examine both variables together. Our research uses logistic regression to calculate an expected value for director and CEO compensation through their determinants while controlling for firm size and year. The expected value is then compared to the actual compensation to determine under or over compensation. These variables are used to create for different cases.

1)  CEOs and Directors are both overcompensated.
2)  CEOs and Directors are both undercompensated.
3)  CEO is overcompensated and Directors are undercompensated.
4)  CEO is undercompensated and Directors are overcompensated.

These four cases are then correlated to firm performance while controlling for determinants of firm performance.

# Methodology

## Director Compensation methodology and variables

### Regression Analysis
       For the Director Compensation analysis we split the firms up by their size category. We decided that smaller firms and larger firms should be
       treated differently. Our reasoning was that different firms with higher market/book valuations would skew the data for smaller firms which could 
       have Board of Director compensation methodologies. After splitting the firms in their repsective bins, we ran a Ridge Regession on our 
       compensation variables (Independant Variables) against Board of Director total compensation (Dependant variable). In each of our regressions
       we had to optimize our model to fit the data. 
       
       Tiny bin size regression parameters:
       - Alpha:
       - K value:
       - r2 result:
       
       Medium bin size regression parameters:
       - Alpha:
       - K value:
       - r2 result:
       
       Big bin size regression parameters:
       - Alpha:
       - K value:
       - r2 result:

### Dependant Variables (Test Set)
- Total Director Compensation

### Independant Variables (Train Set)
#### Numeric Data
-Other Compensation
- Non Equity Incentives
- Cash Fees
- Stock Awards
- Option Awards
- Total Other Compensation
- Total Non Equity Incentives
- Total Cash Fees
- Total Stock Awards
- Total Option Awards
- Market Value of the Firm
- Total Fiscal Market Value
- Liquidity
- Net Income
- Number of Employees
- Debt to Equity Ratio
- Assets in Place
- Capex by Assets
- Return on Equity
#### Categorical data
- Size Category
       - Tiny
       - Medium
       - Big

       
## Director Compensation methodology and variables
### Independant Variables (Train Set)
#### Numeric Data
#### Categorical data


### Regression Analysis
### Dependant Variables (Test Set)

- Comp variables
- Determinants
- Regression while controlling firm size

       Tiny bin size regression parameters:
       - Alpha:
       - K value:
       - r2 result:
       
       Medium bin size regression parameters:
       - Alpha:
       - K value:
       - r2 result:
       
       Big bin size regression parameters:
       - Alpha:
       - K value:
       - r2 result:

Overpayment:
- Predict after train
- Variable creation
- Case production

Correlation:
- Control variables
- Use of overpayment
