# The Process:

Prior literature has individually examined the impact of Director compensation and CEO compensation on firm 
performance, but there are less studies that examine both variables together. Our research uses logistic 
regression to calculate an expected value for director and CEO compensation through their determinants while 
controlling for firm size and year. The expected value is then compared to the actual compensation to determine 
under or over compensation. These variables are used to create for different cases.

1)  CEOs and Directors are both overcompensated.
2)  CEOs and Directors are both undercompensated.
3)  CEO is overcompensated and Directors are undercompensated.
4)  CEO is undercompensated and Directors are overcompensated.

These four cases are then correlated to firm performance after accounting for controls.


# Methodology

## Director Compensation methodology and variables
### Regression Analysis
Through our research, we learned that firms of different sizes have varrying payout structures to their executives and directors. We split the firms into 4 different size categories to allow for individual treatment during the regressions. Small firms were catagorized with a maximum market cap at $10 billion, followed by medium at $200 billion, large anything over $200 billion, and huge at ___.

After splitting the firms in their respective bins, we ran a Ridge Regression 
on our determinates for compensation (Independent Variables) against Board of Director total compensation (Dependent 
variable). In each of our regressions we had to optimize our model to fit the data.

The model was unable to fit the firms in the "huge" bin within any degree of accuracy. This suggests that different determinates govern director compensation at giant firms. If we were to re-run the analysis, we would do more research to find different determinates. For the time being, we decided to omit the data because no meaningful predications could be made.

We decided to emit the traditional "Huge" bin and re-binned to three categories so we where left with small, 
medium, and large firms. Small being from 0 to 10 billion dollars, Medium being from 10 billion to 200 billion, 
and then Large is 200 billion onwards.  

Small bin size regression parameters:
- Alpha: 118
- K value: 64
- r2 result: 0.472074

Medium bin size regression parameters:
- Alpha: 100
- K value: 95
- r2 result: 0.618721

Large bin size regression parameters:
- r2 result: -0.072973

       
## CEO Compensation methodology and variables
### Regression Analysis
For the CEO Compensation analysis we created new variables to identify how much "Power" a CEO has. We determined 
four variables to use in our analysis. The CEO Ownership Ratio, CEO Ownership Power, Years Served, and Prestige 
Power. In our regression we split the firms up by their size category. We decided that smaller firms and larger 
firms should be treated differently. Our reasoning was that different firms with higher market/book valuations 
would skew the data for smaller firms which could have different CEO compensation methodologies. After splitting 
the firms in their respective bins, we ran a Ridge Regression on our compensation variables (Independent 
Variables) against Board of Director total compensation (Dependent variable). In each of our regressions we had 
to optimize our model to fit the data. 

Small bin size regression parameters:
- Alpha: 0.001
- K value: 96
- r2 result: 0.731653

Medium bin size regression parameters:
- Alpha: 19
- K value: 96
- r2 result: 0.68396

Large bin size regression parameters:
- Alpha: 663
- K value: 87
- r2 result: 0.887327

### Dependent Variables (Test Set)
- Total CEO Compensation
### Independent Variables (Train Set)
### Created Variables
- ownershipRatio
- ownershipPower
- yearServed
- prestigePower
#### Numeric Data
- CEO Age
- Stock Awards
- Market Value
#### Categorical data
- Size Category
       - Tiny
       - Medium
       - Big



Over payment:
- Predict after train
- Variable creation
- Case production

Correlation:
- Control variables
- Use of over payment
