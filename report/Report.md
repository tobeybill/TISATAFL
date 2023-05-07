# <p style="text-align: center;"> Firm performance relative to CEO and BOD compensation </p>

## <p style="text-align: center;"> FIN - 377 Final Project Report </p>
### <p style="text-align: center;"> Professor: Don Bowen Ph.D </p>
### <p style="text-align: center;"> By: Rha Overstreet, Alex Romanowski, Tobey Bill, Anna Harvey </p>

---

## Abstract

This study examines the impact of CEO and Director compensation and firm performance. After conducting regression on a series of determinants to determine if CEOs and directors were overcompensated, four use cases were created with the following hypotheses:
1. Both CEOs and directors are overcompensated: Firm performance will suffer due to backscratching and underperforming executives.
2. The CEO is overcompensated and directors are undercompensated: Firm performance will excel due to a more qualified CEO and strong controls over the board of directors.
3. The CEO is undercompensated and directors are overcompensated: Firm performance will suffer because the directors are self serving and less motivated to replace the CEO in fear of loosing their compensation.
4. Both CEOs and directors are undercompensated: Firm performance will excel because the firm has strong governance to prevent overcompensation.

These hypotheses were correlated with a firm performance variable that was created through regression using a series of control determinants. The study found that large firms, overpayment is negatively correlated with firm performance; small firms, overpayment is positively correlated with firm performance, and the medium firms are right in the middle. There were several sources of error contributing to the many missing variables from the WRDS database for the S&P 500 and we had too few variables to conclude a concrete result. Further analysis should be conducted to explore more variables that are not a part of the WRDS dataset that we could have also used to have a deeper analysis.

---

## Introduction
Executive compensation has ballooned over the past 40 years with an increase in pay of 1,167% relative to the growth of the S&P 500 at 741% (Bouteska & Mefteh-Wali). This discrepancy has raised many eyebrows in academia, the public, and media. If executive compensation growth has outweighed the growth of the market are the higher ups really performing better or have they colluded with their governing bodies, the board of directors, to pay themselves an outsized share of the profits? Furthermore, what impact does this have on firm performance?

<img src="/images/ceo_comp.JPG?raw=true"/>

**[CEO pay has skyrocketed 1,322% since 1978](https://www.epi.org/publication/ceo-pay-in-2020/)**

Dah and Frya found that directors were overcompensated more often than not, with their average overcompensation exceeding their average undercompensation, leading to reduced CEO turnover sensitivity and a decrease in CEO pay-for-performance sensitivity (Dah & Frya). This indicates that overpaid directors may be hesitant to remove CEOs for fear of decreasing their own pay. Additionally, overpaid directors may be less likely to dock CEO pay for poor performance in case the CEO retaliates by docking their pay as well.

Another study touches on the determinants of CEO compensation through 2006-2016. The study found several categories of determinants that impacted compensation: accounting and performance, CEO power, and governance. CEO pay had a higher correlation on firm performance in more mature firms when compared to younger firms. High CEO power over the board led to an increase in compensation, while strong governance led to a decrease in compensation (Bouteska & Mefteh-Wali). 

A paper on the impact of CEO compensation and director compensation on firm performance found a strong positive correlation between CEO and director compensation. The paper also found a relationship between overcompensation and underperformance; concluding that overcompensation is due to poor governance and backscratching (Brick, Palmon, & Wald). 

This research prompted us to further explore these relationships and focus on four cases of CEO and director compensation. Through our analysis, we hope to add further evidence of the impact of executive compensation on firm performance.

---


## Data and Variables
**We utilized the Wharton Research Data Services for our data sets** All data regarding director and CEO compensation and demographics came from Execucomp. Firm accounting variables and other firm specific information came **from Compustat and CRSP.** We cross referenced multiple studies to find determinants of CEO and director compensation as well as firm performance. Our sample size comprised of firms in the S&P500 from 2010 - 2019. We chose 2010-2019 to avoid the corporate scandals of the early 2000's and the impact of COVID on the market.

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

---
## Process
Prior literature has individually examined the impact of Director compensation and CEO compensation on firm 
performance, but there are less studies that examine both variables together. Our research uses logistic 
regression to calculate an expected value for director and CEO compensation through their determinants while 
controlling for firm size and year. The expected value is then compared to the actual compensation to determine 
under or over compensation. These variables are used to create for different cases.

1)  CEOs and Directors are both overcompensated.
2)  CEO is overcompensated and Directors are undercompensated.
3)  CEO is undercompensated and Directors are overcompensated.
4)  CEOs and Directors are both undercompensated.

These four cases are then correlated to firm performance after accounting for controls.

---
## Methodology

### Regression Analysis for Director and CEO Compensation

The regressions for director and CEO compensation were ran separately, but the overarching process is the same.

Through our research, we learned that firms of different sizes have varying payout structures to their executives and directors. We split the firms into 3 different size categories to allow for individual treatment during the regressions. Small firms were categorized with a maximum market cap at $10 billion, followed by medium at $200 billion, and large anything over $200 billion.

After splitting the firms in their respective bins, we ran a Ridge Regression 
on our determinants for compensation (Independent Variables) against director/CEO total compensation (Dependent 
variable). 

We used GridSearchCV to optimized each our models for the alpha and K value. After many iterations, the best_alpha function was used to pick the set of parameters that fit the data the best. 

**Removed heading**

''' {python}

    numer_pipe = make_pipeline(SimpleImputer(strategy="mean"), StandardScaler())
    cat_pipe = make_pipeline(OneHotEncoder())

    preproc_pipe = make_column_transformer(
        (numer_pipe, make_column_selector(dtype_include=np.number)),
        (cat_pipe, ['gender']),
        remainder="drop",
    )

    ridge_pipe = Pipeline([
        ('preprocessor', preproc_pipe),
        ('ridge', Ridge())
    ])
    alphas = list(np.linspace(0, 300, 25))
    parameters = {'ridge__alpha': alphas}

    grid_search = GridSearchCV(estimator=ridge_pipe, 
                            param_grid=parameters,
                            cv=cv,
                            scoring='r2',
                            error_score='raise')

    results = grid_search.fit(X_train, y_train)
'''

This above code was used to start finding the applicable alpha for each group. 

Despite optimizing our regression, the director model was unable to fit the firms in the "huge" bin within any degree of accuracy. This suggests that different determinants govern director compensation at giant firms. If we were to re-run the analysis, we would do more research to find different determinants. For the time being, we decided to omit the data because no meaningful predictions could be made.
 
__Board of Directors Results__

Small bin size regression parameters:
- K=79
- Alpha=202
- R2 result: 0.469471

Medium bin size regression parameters:
- K=95
- Alpha=100
- R2 result: 0.618721

Large bin size regression parameters:
- K=79
- Alpha=0.0001
- R2 result: 0.227747

__CEO results __

Small bin size regression parameters:
- K =96
- Alpha=0.01
- R2 result:0.731653


Medium bin size regression parameters:
- K=96 
- Alpha=19
- R2 result: 0.68396

Large bin size regression parameters: (to prevent overfitting these variables were omitted for large bin size('total_curr','salary', 'bonus', 
        'stock_awards', 'option_awards', 'othcomp')
- K=85
- Alpha=559
- R2 result: 0.887815

------

## Overpayment Predictions

Once we fit the models to the training data set, we used them to predict compensation for our holdout data. That provided us with a predicted compensation. We used this variable to create an overpayment variable.

Overpayment = Actual Pay / Predicted Pay

**This was done by **
```{python}
```

-----

## Firm Performance Score

We needed a measure of performance to determine the effects of compensation on it. Based on our initial research, we were originally going to use Tobin's Q as our measure, but reviewing *Determinants of Firm Performance: A Subjective Model (Sigo, 2020)* prompted us to take the analysis one step further. Because the review outlines many different factors that impact firm performance, we decided to create our own performance score for each firm in each year and compare that score to the over/underperforming variables we had calculated previously. The process for doing that involved the following:

1. Determining relevant measures to firm performance (see firm performance variables above)
    1. Sigo segmented firm performance measures into 9 categories ranging from Profitability Performance to Social Performance, these categories were then broken down into the various measures that corresponded to them, so we chose those that were contained within the data available to us
1. Pulled neccessary accounting variables from Compustat Annual Fundamentals dataset
2. Created methods to calculate the measures from the accounting variables
3. Created a dataframe that contained each (Firm, Year) and its firm performance measures (calculated by applying the previously-created methods to each firm's accounting variables in that year)
    4. For measures such as stock price performance and volatility, data was pulled from Yahoo Finance
5. Assign weights to each of the measures for the overall performance score calculation
    1. We ran a linear regression to fit the determinants of firm performance to Tobin's Q, often considered an indicator of firm performance
    2. Once the regression was fit, we utilized the independent variable coefficients of the regression as our weights
6. Calculate performance score for each (Firm, Year)
    1. Using `StandardScaler()`, data is standardized by removing the mean and scaling to unit variance
    2. New values are multiplied by their corresponding weights, then summed by row to determine overall score

```{python}
performance_score = firm_performance
firm_performance = firm_performance.dropna(subset=['tobinsQ'])
y = firm_performance.tobinsQ
firm_performance = firm_performance.drop('tobinsQ',axis=1)

scores_df = firm_performance[['tic', 'fyear']].copy()

firm_performance = firm_performance.drop('fyear',axis=1)

rng = np.random.RandomState(0)
X_train, X_test, y_train, y_test = train_test_split(firm_performance, y, random_state=rng)

numer_pipe = make_pipeline(SimpleImputer(), 
                           StandardScaler())

preproc_pipe = ColumnTransformer(
    [("num_impute", numer_pipe, make_column_selector(dtype_include=np.number)),]
    , remainder = 'drop'
)

linear_pipe = make_pipeline(preproc_pipe,
                           LinearRegression())

results = linear_pipe.fit(X_train, y_train)

coefficients = linear_pipe.named_steps['linearregression'].coef_

coef_df = pd.DataFrame({'metric':X_train.columns[1:],
                        'weight':coefficients})
                        
weights = np.abs(coefficients) / np.sum(np.abs(coefficients))

weight_df = pd.DataFrame({'metric':X_train.columns[1:],
                        'weight':weights})

weight_dict = weight_df.set_index('metric').T.to_dict('list')

scaler = StandardScaler()
performance_score = pd.DataFrame(scaler.fit_transform(performance_score.iloc[:, 2:]), columns=performance_score.iloc[:, 2:].columns)

for metric in weight_dict:
    performance_score[metric] = performance_score[metric] * weight_dict[metric]
    
performance_score['Performance Score'] = performance_score.sum(axis=1)
```
Once the score is calculated for each firm in our prediction years they were correlated with the over/undercompensating variable for the same (Firm, Year). The relationship was also graphed for each firm size, both for CEOs and directors.

Lastly, we determined the average performance score present for firms within each case out of those outlined in the abstract. As discussed below, this provided us insight into how firms of each size fared with over and undercompensation of their CEOs and directors.

---
## Results

After running the correlations between the overpayment variables and the firm performance score for each case, we found the following results.

### Correlation Tables

<img src="/images/corr_ceo.png?raw=true"/>

We found that there was very strong correlation between CEO overpayment and firm performance for small firms, and an equally as strong negative correlation for the larger firms. For those in the mid-size, there wasn't much change. 

<img src="/images/corr_bod.png?raw=true"/>

We found the opposite for directors, that there was very strong correlation between BOD overpayment and firm performance for large firms but a negative correlation for overpayment for the small ones.


### Correlation Graphs

<img src="/images/corr_CEO_graph.png?raw=true"/>

<img src="/images/corr_BOD_graph.png?raw=true"/>

Visually, it can be observed that there is a much larger scale for overcompensation on the part of the CEOs, wich an outlier being above 1600% of predicted pay. On the BOD side, a separate outlier sits at roughly 800% of predicted pay. Additionally, it appears that medium-sized firms are most responsible for CEO overpayment wheras smaller firms are more responsible for director overpayment. In both cases, firm performance for larger firms seems to be less volatile than that for the other two size categories.


### Case Analysis

<img src="/images/cases_desc.png?raw=true"/>
<img src="/images/avg_perf.png?raw=true"/>

Separating out our various firms in the above four cases, we found that large firms with an underpaid CEO and overpaid BOD perform the best and small firms with underpaid CEO and BOD perform the worst. It is also important to note that, for large firms, overpayment of the CEO results in poor performance while for the other two sizes it improves firm performance. For small firms especially, the overpayment of the CEO very heavily impacts the firm performance. 

---

## Conclusion

This supports our hypothesis
1. Both CEOs and directors are overcompensated: Firm performance will suffer in large firms due to backscratching and underperforming executives, but is improved for mid-size and small firms.
2. The CEO is overcompensated and directors are undercompensated: Firm performance will excel in mid-size and small firms due to a more qualified CEO and strong controls over the board of directors, but will be hurt in large firms.
3. The CEO is undercompensated and directors are overcompensated: Firm performance will suffer in small firms because the directors are self serving and less motivated to replace the CEO in fear of loosing their compensation, but will improve in large and mid-size firms.
4. Both CEOs and directors are undercompensated: Firm performance will excel in large and mid-size firms because the firm has strong governance to prevent overcompensation, but will suffer for the smaller size firms due to lack of adequate motivation.

--- 
## Citations
1.  Mustafa A. Dah, Melissa B. Frye, "Is board compensation excessive?", Journal of Corporate Finance, Volume 45, 2017, Pages 566-585, ISSN 0929-1199,
https://doi.org/10.1016/j.jcorpfin.2017.06.001.(https://www.sciencedirect.com/science/article/pii/S0929119917303589)
2.  Ahmed Bouteska, Salma Mefteh-Wali, "The determinants of CEO compensation: new insights from United States", Journal of Applied Accounting Research, 23 June 2021, vol. ahead-of-print, pages 663-686, ISSN 09675426, https://www.emerald.com/insight/content/doi/10.1108/JAAR-08-2020-0176/full/html#abstract
3.  Cordeiro, James J., and Rajaram Veliyath. "Beyond Pay for Performance: A Panel Study of the Determinants of CEO Compensation." American Business Review, vol. 21, no. 1, 2003, pp. 56-66. ProQuest, https://www.proquest.com/scholarly-journals/beyond-pay-performance-panel-study-determinants/docview/216292921/se-2.Ivan E. Brick, Oded Palmon, John K. Wald,
4.  Ivan E. Brick, Oded Palmon, John K. Wald, "CEO compensation, director compensation, and firm performance: Evidence of cronyism?", Journal of Corporate Finance, Volume 12, Issue 3, 2006, Pages 403-423, ISSN 0929-1199, https://doi.org/10.1016/j.jcorpfin.2005.08.005. (https://www.sciencedirect.com/science/article/pii/S0929119905000738) 
5. Sigo, Marxia Oli, Determinants of Firm Performance: A Subjective Model (August 1, 2020). 14th Annual Conference of Financial Economics and Accounting, Forthcoming, Available at SSRN:  https://ssrn.com/abstract=3665334
