# <p style="text-align: center;"> Firm performance relative to CEO and BOD compensation </p>

## <p style="text-align: center;"> FIN - 377 Final Project Report </p>
### <p style="text-align: center;"> Professor: Don Bowen Ph.D </p>
### <p style="text-align: center;"> By: Rha Overstreet, Alex Romanowski, Tobey Bill, Anna Harvey </p>

---

## Abstract

This study examines the impact of CEO and Director compensation and firm performance. We conducted a regression analysis on a set of determinants derived from academic literature regarding C-suite and Director compensation. Our four use cases are:

1. Both CEOs and directors are overcompensated. Firm performance will suffer due to backscratching and underperforming executives.

2. The CEO is overcompensated and directors are undercompensated. Firm performance will excel due to a more qualified CEO and strong influence over the board of directors.

3. The CEO is undercompensated and directors are overcompensated. Firm performance will suffer because the directors are self-serving and less motivated to replace the CEO in fear of losing their compensation.

4. Both CEOs and directors are undercompensated. Firm performance will excel due to strong firm governance, which prevents overcompensation.



These cases were correlated with a firm performance variable that we created using the aforementioned determinants. We split our dataset into three bins according to market size. Our study found that large firms have a negative correlation between CEO overcompensation and firm performance. Small firms have a positive correlation between CEO overcompensation and firm performance. Medium firms did not have a correlation between overcompensation and performance. In our study we have determined possible error sources. The datasets gathered from WRDS had missing fields which required either dropping the set or imputing missing variables in our regressions. Further analysis should be done with a larger data set spanning a longer set of years. Note: In this study we used companies listed on the S&P500.


---



## Introduction

Executive compensation has outperformed public markets in the past 40 years. There has been an increase in compensation of about 1167 points while the relative growth of the S&P 500 has been 741 points (Bouteska & Mefteh-Wali). This disparity has shocked academics, the media, and members of the public. C-suite and Directors keep making more money, even in economic down cycles. From this observation, it can be inferred that there is possible collusion. Is upper management outperforming the market or is their collusion within those governing bodies? The question we aim to answer is: What is the effect of overcompensation on firm performance, taking into account firm size?

<img src="/images/ceo_comp.JPG?raw=true"/>

**[CEO pay has skyrocketed 1,322% since 1978](https://www.epi.org/publication/ceo-pay-in-2020/)**

Dah and Frya found that directors are overcompensated more often than not, with their average overcompensation exceeding their average undercompensation, leading to reduced CEO turnover sensitivity and a decrease in CEO pay-for-performance sensitivity (Dah & Frya). This indicates that overpaid directors may be hesitant to remove CEOs to guard against a decrease in their compensation. Additionally, overpaid directors may be reluctant to reduce CEO pay for poor performance. This is most likely due to the CEOs' capability of reducing the Directors' compensation.


Another study touches on the determinants of CEO compensation from 2006 to 2016. The study found several determinants that impacted compensation. These determinants can be found in accounting performance indicators, perceived CEO power, and CEO governance. CEO pay had a higher correlation with mature firms' performance. High CEO power over the board led to an increase in compensation, while strong governance led to a decrease in compensation (Bouteska & Mefteh-Wali). 


A paper on the impact of CEO compensation and director compensation on firm performance found a strong positive correlation between CEO and director compensation. The paper also found a relationship between overcompensation and underperformance, concluding that overcompensation is due to poor governance and backscratching/collusion (Brick, Palmon, & Wald). 


This research prompted us to further explore these relationships and focus on the above-mentioned cases of CEO and director compensation. Through our analysis, we hope to add further evidence towards the study of executive compensation and firm performance.

---


## Data and Variables
**We utilized the Wharton Research Data Services for our data sets** All data regarding director and CEO compensation and demographics came from Execucomp. Firm accounting variables and other firm specific information came **from Compustat.** We cross referenced multiple studies to find determinants of CEO and director compensation as well as firm performance. Our sample size comprised of firms in the S&P500 from 2010 - 2019. We chose 2010-2019 to avoid the corporate scandals of the early 2000's and the impact COVID-19 had on the market.

### BOD Compensation and Determinants
Director compensation was derived as their total compensation. Including cash, value of stock options and option awards, non-equity incentive plan compensation, change in pension value and "nonqualified" deferred compensation earnings, and all other compensations.

We used accounting based firm valuations and market performance as determinants for predicting Board of Directors compensation. The accounting variables and compensation variables (not including total compensation) are lagged by one year.  We are assuming that current total compensation is impacted by previous years' performance. The accounting metrics of a firm are resilient to equity market changes. These metrics focus on internal firm performance, which will reduce the impact a strong market position will have on predicted compensation. A strong market artificially inflates firm values, even if the firm is not doing well internally. We included market performance determinants in our analysis because BOD packages usually contain some equity incentives (Dah and Frye).



### CEO Compensation and Determinants

The CEO variables were also lagged by one year, not including total compensation. We determined past compensation can be used as an indicator for future compensation. CEO determinants are a combination of created variables and stock awards. We created an Ownership Ratio, Ownership Power, Year Served, and Prestige determinants. The Ownership Ratio is the CEO Stock Awards divided by BOD Stock Awards. These variables represent the equity power a CEO holds over a Board of Directors. If a CEO holds more equity than the board, then they hold more power over the company and have a greater influence on the board. We then created a determinant called Ownership Power. This is a binary categorical variable. This variable indicated whether the CEO Ownership Ratio was above the CEO Ownership Ratio median. We predict that CEOs with a higher ownership ratio will have more control over the firm and thus more influence on their pay. For Years Served, we took the difference between the year the CEO was on-boarded and the recorded year. CEOs that serve longer terms are more experienced and are more likely to receive higher pay. We based Prestige Power off of Years Served. Prestige power is a binary categorical variable that indicates whether time served is above the median. This implies a CEO can gain prestige power during their term (Bouteska and Mefteh-Wali)



### Determinants of Firm Performance

The review written by Sigo explores a wide variety of contributing factors to firm performance: profitability performance, growth performance, market value performance of the firm, customer satisfaction, employee satisfaction, environmental audit performance, corporate governance performance and social performance. Although this may seem exhaustive, the paper did not actually test any of these variables as controls. For our analysis, we focused on the profitability performance, growth performance, and market value performance due to their availability in the compustat dataset. All of these determinants are later used to predict firm performance.



### Exploratory Data Analysis

After querying the data from WRDS, we did an Exploratory Data Analysis or EDA on our data frames. Our EDA leads us to dropping variables deemed unnecessary in our analysis, imputing data into missing or NaN data fields, and creating new variable identifiers. 



The data sets that were queried from WRDS were very extensive. We did not have use for all of the variables in the data sets, and selected the ones we determined to be pertinent to our project based on the literature we read. We renamed variables to have more comprehensive labels. For missing data, we imputed values depending on the variable case. For the variables we did not create, we imputed missing values with that variables mean. The imputed means were done according to market value bins. For example, the Tiny firms would not be imputed with the Large firms means. We had to normalize the variables we created. Some of the divisions resulted in NaN and 'inf' values. We understood that the NaN results came from dividing zero and 'inf' was the result of dividing by zero. We imputed the NaN results to zero and capped the 'inf' results to the maximum value of that variable set. 



Out of the two CEO total compensation values, we kept the variable that used the Black Scholes Model to value the options held by the CEO (TDC1).



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

A majority of the prior research on executive compensation and firm performance has either been CEO or Director compensation. They are not usually studied in tandem. Our research uses a Ridge model to calculate an expected value for director and CEO compensation through their determinants while controlling for firm size and year. The expected value is then compared to the actual compensation to determine under or over compensation. In our four performance analyses, we correlate them to firm performance after accounting for the control variables we created.



Four cases

1)  CEOs and Directors are both overcompensated.

2)  CEO is overcompensated and Directors are undercompensated.

3)  CEO is undercompensated and Directors are overcompensated.

4)  CEOs and Directors are both undercompensated.



---

## Methodology



### Regression Analysis for Director and CEO Compensation



The regressions for director and CEO compensation were run separately, but the overarching process is the same. We used SciKit Learn libraries to create our data pipelines and optimize our hyper-parameters.​



Through our research, we learned that firms of different sizes have varying payout structures for their executives and directors. We split the firms into 3 different size categories to allow for individual treatment during the regressions. Small firms were categorized with a maximum market cap at $10 billion, followed by medium at $200 billion, and large anything over $200 billion. After splitting the firms into their respective bins, we ran a Ridge Regression on our determinants for compensation (Independent Variables) against director/CEO total compensation (Dependent variable). We used GridSearchCV to optimize each of our models for the alpha and K values. After many iterations, the best_pipe function was used to pick the set of parameters that fit the data the best. 

**Removed heading**

```{python}

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
```

This above code was used to start finding the applicable alpha for each group. 

Despite optimizing our regression, the director model was unable to fit the firms in the "huge" bin within any degree of accuracy. This suggests that different determinants govern director compensation at giant firms. If we were to re-run the analysis, we would do more research to find more applicable determinants. For the time being, we decided to omit the data because no meaningful predictions could be made.
 
__Board of Directors Results__

Small bin size regression parameters:
- K = 79
- Alpha = 202
- R2 result: 0.469471

Medium bin size regression parameters:
- K = 95
- Alpha = 100
- R2 result: 0.618721

Large bin size regression parameters:
- K = 79
- Alpha = 0.0001
- R2 result: 0.227747

__CEO results __

Small bin size regression parameters:
- K = 96
- Alpha = 0.001
- R2 result:0.731653

Medium bin size regression parameters:
- K = 19 
- Alpha = 19
- R2 result: 0.68396

Large bin size regression parameters: (to prevent overfitting these variables were omitted for large bin size('total_curr','salary', 'bonus', 
        'stock_awards', 'option_awards', 'othcomp')
- K = 85
- Alpha = 559
- R2 result: 0.887815

------

## Overpayment Predictions

After fitting our models to the training set we predicted compensation on out holdout data. After getting our predicted compensations we created the our overcompensation variable.

Overpayment = Actual Pay / Predicted Pay

**The following code for the CEO payment in small firm sizes was repeated for medium and large firms and all three sizes for director payment**
```{python}
small_ceo_df = pd.read_csv('../Saved/small_ceo_df.csv')
pred_small_ceo_df = pd.read_csv('../Saved/pred_small_ceo_df.csv')
small_ceo_df['prediction'] = pred_small_ceo_df['prediction']
small_ceo_df['over_under_comp'] = small_ceo_df['tdc1']/pred_small_ceo_df['prediction']
```

-----

## Firm Performance Score

We needed a measure of performance to determine the effects of compensation on firm performance. Based on our initial research, we were originally going to use Tobin's Q as our measure, but reviewing *Determinants of Firm Performance: A Subjective Model (Sigo, 2020)* prompted us to take the analysis one step further. Because the review outlines many different factors that impact firm performance, we decided to create our own performance score for each firm in each year and compare that score to the performance variables we had calculated previously. The process for doing that involved the following:

1. Determining relevant measures to firm performance (see firm performance variables above)
    1. Sigo segmented firm performance measures into 9 categories ranging from Profitability Performance to Social Performance, these categories were then broken down into the various measures that corresponded to them, so we chose those that were contained within the data available to us
2. Pulled neccessary accounting variables from Compustat Annual Fundamentals dataset
3. Created methods to calculate the measures from the accounting variables
4. Created a dataframe that contained each (Firm, Year) and its firm performance measures (calculated by applying the previously-created methods to each firm's accounting variables in that year)
    1. For measures such as stock price performance and volatility, data was pulled from Yahoo Finance
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

The weights used are reflected in the following graph:

<img src="/images/weights_graph.png?raw=true"/>

We correlated the compensation variables with each calculated score for the same firm and year. The relationship was graphed for each of the size bins for both CEOs and Directors.

Our final step was determining the average performance score for each firm used in our analysis, firms listed on the S&P 500 from 2010 to 2019. We can now gain insight on how firms of different sizes performed with over and under compensated executive management.

```{python}
def assignCase(df):
    df = df.dropna()
    cases = [
        (df['over_under_ceo'] >= 1) & (df['over_under_bod'] >= 1), # Case 1
        (df['over_under_ceo'] >= 1) & (df['over_under_bod'] <= 1), # Case 2
        (df['over_under_ceo'] <= 1) & (df['over_under_bod'] >= 1), # Case 3
        (df['over_under_ceo'] <= 1) & (df['over_under_bod'] <= 1) # Case 4
    ]
    names = ['Case 1', 'Case 2', 'Case 3', 'Case 4']
    df['Case'] = np.select(cases, names, default = np.nan)
    return df
    
combined_bod_ceo = pd.concat([small_bod_ceo, med_bod_ceo, large_bod_ceo], axis=0)
combined_bod_ceo = assignCase(combined_bod_ceo)

combined_avg_perf = combined_bod_ceo.groupby(['Firm Size', 'Case']).agg({'Performance_Score': 'mean', 'Case': 'size'})
combined_avg_perf = combined_avg_perf.rename(columns={'Performance_Score':'avg_perf_score','Case':'count'})
```

---
## Results

After running the correlations between the compensation variables and the firm performance score for each case, we found the following results.

### Correlation Tables

|Firm Size|Correlation|
|---------|-----------|
| Small   | 0.241048  |
| Medium  | 0.027822  |
| Large   | 0.077771  |

There is a very strong correlation between CEO overpayment and firm performance for small firms, and an equally as strong negative correlation for the larger firms. For those in the mid-size, there wasn't much change. 

|Firm Size|Correlation|
|---------|-----------|
| Small   | -0.251290 |
| Medium  | -0.047808 |
| Large   | -0.027887 |

We found the opposite for directors. There is a very strong correlation between BOD overpayment and firm performance for large firms but a negative correlation for overpayment for the small ones.


### Correlation Graphs

<img src="/images/corr_ceo_graph.png?raw=true"/>

<img src="/images/corr_BOD_graph.png?raw=true"/>

There is a larger scale for CEO compensation than director compensation with an outlier of CEO compensation above 1600% of predicted pay. On the BOD side, a separate outlier sits at roughly 800% of predicted pay. Additionally, it appears that medium-sized firms are responsible for the majority of CEO overpayment whereas smaller firms are more responsible for director overpayment. In both cases, firm performance for larger firms seems to be less volatile than that for the other two size categories. That said, it is possible that large firms are less volitile due to the determinants we picked. Because the accounting variables for large firms are so much greater than the other size firms, the model may have had more tolerance for change in CEO compensation.



### Case Analysis

|Case     |Description                    |
|---------|-------------------------------|
| Case 1  |CEO and BOD both overpaid      |
| Case 2  |CEO overpaid and BOD underpaid |
| Case 3  |CEO underpaid and BOD overpaid |
| Case 4  |CEO and BOD both underpaid     |


|Firm Size|Case| avg_perf_score | count |
|---------|----|----------------|-------|
| Large   | 1  |  0.520715      | 31    |
|         | 2  |  0.638213      | 26    |
|         | 3  |  1.755433      | 3     |
|         | 4  |  1.784764      | 4     |
| Medium  | 1  |  0.298682      | 583   |
|         | 2  |  0.151899      | 149   |
|         | 3  |  0.054874      | 237   |
|         | 4  |  0.078295      | 124   |
| Small   | 1  |  0.077480      | 101   |
|         | 2  |  0.219309      | 29    |
|         | 3  |  -0.481463     | 64    |
|         | 4  |  -0.279931     | 16    |

Separating out our various firms in the above four cases, we found that large firms with an underpaid CEO and overpaid BOD perform the best. Small firms with underpaid CEO and BOD perform the worst. It is also important to note that, for large firms, overpayment of the CEO results in poor performance while it improves firm performance for medium and small firms. Small firms had heavy positive impacts after overpaying their CEO's.

---

## Conclusion

Executive management compensation has been inflating at a rate not reflected in worker salaries, traditional firm performance, and firm market performance. The drastic increase in executive compensation has often called the legitimacy of the impact these positions have on firm performance into question. Does paying executive management abnormally large salaries really make an impact? Through our study we have found that, in certain cases, there is a significant impact.


Our results have supported our hypothesis in the following ways.

1. Both CEOs and directors are overcompensated. Firm performance will suffer in large firms due to backscratching and underperforming executives, although performance is improved for mid-size and small firms.

2. The CEO is overcompensated and directors are undercompensated. Firm performance will excel in mid-size and small firms due to a more qualified CEO and strong control over the board of directors, but will be hurt in large firms.

3. The CEO is undercompensated and directors are overcompensated. Firm performance will suffer in small firms because the directors are self-serving and less motivated to replace the CEO in fear of losing their compensation. Performance improves in large and mid-size firms.

4. Both CEOs and directors are undercompensated. Firm performance will excel in large and mid-size firms because the firm has strong governance to prevent overcompensation, but will suffer for the smaller-sized firms due to lack of adequate motivation.

--- 
## Citations
1.  Mustafa A. Dah, Melissa B. Frye, "Is board compensation excessive?", Journal of Corporate Finance, Volume 45, 2017, Pages 566-585, ISSN 0929-1199,
https://doi.org/10.1016/j.jcorpfin.2017.06.001.(https://www.sciencedirect.com/science/article/pii/S0929119917303589)
2.  Ahmed Bouteska, Salma Mefteh-Wali, "The determinants of CEO compensation: new insights from United States", Journal of Applied Accounting Research, 23 June 2021, vol. ahead-of-print, pages 663-686, ISSN 09675426, https://www.emerald.com/insight/content/doi/10.1108/JAAR-08-2020-0176/full/html#abstract
3.  Cordeiro, James J., and Rajaram Veliyath. "Beyond Pay for Performance: A Panel Study of the Determinants of CEO Compensation." American Business Review, vol. 21, no. 1, 2003, pp. 56-66. ProQuest, https://www.proquest.com/scholarly-journals/beyond-pay-performance-panel-study-determinants/docview/216292921/se-2.Ivan E. Brick, Oded Palmon, John K. Wald,
4.  Ivan E. Brick, Oded Palmon, John K. Wald, "CEO compensation, director compensation, and firm performance: Evidence of cronyism?", Journal of Corporate Finance, Volume 12, Issue 3, 2006, Pages 403-423, ISSN 0929-1199, https://doi.org/10.1016/j.jcorpfin.2005.08.005. (https://www.sciencedirect.com/science/article/pii/S0929119905000738) 
5. Sigo, Marxia Oli, Determinants of Firm Performance: A Subjective Model (August 1, 2020). 14th Annual Conference of Financial Economics and Accounting, Forthcoming, Available at SSRN:  https://ssrn.com/abstract=3665334
