# The Process:

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

----- 

# Methodology

## Regression Analysis for Director and CEO Compensation

The regressions for director and CEO compensation were ran separately, but the overarching process is the same.

Through our research, we learned that firms of different sizes have varying payout structures to their executives and directors. We split the firms into 3 different size categories to allow for individual treatment during the regressions. Small firms were categorized with a maximum market cap at $10 billion, followed by medium at $200 billion, and large anything over $200 billion.

After splitting the firms in their respective bins, we ran a Ridge Regression 
on our determinants for compensation (Independent Variables) against director/CEO total compensation (Dependent 
variable). 

We used GridSearchCV to optimized each our models for the alpha and K value. After many iterations, the best_alpha function was used to pick the set of parameters that fit the data the best. 

## Code Snippet
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

Despite optimizing, the director model was unable to fit the firms in the "huge" bin within any degree of accuracy. This suggests that different determinants govern director compensation at giant firms. If we were to re-run the analysis, we would do more research to find different determinants. For the time being, we decided to omit the data because no meaningful predictions could be made.
 


__Director Results__

Small bin size regression parameters:
- Alpha: 118
- K value: 64
- r2 result: 0.472074

Medium bin size regression parameters:
- Alpha: 100
- K value: 95
- r2 result: 0.618721

Large bin size regression parameters:
- Alpha=0.0001
- K value: 79
- r2 result: 0.227747


__Ceo Results__

Small bin size regression parameters:
- Alpha: 0.001
- K value: 96
- r2 result: 0.731653

Medium bin size regression parameters:
- Alpha: 0.001
- K value: 86
- r2 result: 0.285019

Large bin size regression parameters:
- Alpha: 555
- K value: 85
- r2 result: 0.887814

------

## Overpayment Predictions

Once we fit the models to the training data set, we used them to predict compensation for our holdout data. That provided us with a predicted compensation. We used this variable to create an overpayment variable.

Overpayment = Actual Pay / Predicted Pay

-----

## Firm Performance Score

We needed a measure of performance to determine the effects of compensation on firm performance. Initially, we were going to use Tobin's Q as our measure of performance. However, literature review done by Sigo prompted us to take the analysis one step further. Because the review outlines so many different factors that impact firm performance, we decided to create our own performance score, predict it on the holdout data, then create an over/underperforming variables based on those predictions.

We ran a linear regression to fit the determinants of firm performance to Tobin's Q. We did this because Tobin's Q is often considered an indicator of firm performance. Once the regression was fit, we found the weights of the independent variable coefficients. These weights were standardized by dividing the absolute value of their weight by the sum of the absolute value of all weights. This was saved as our standardized weight variable. The original coefficients were standardized with the standard scalar function. The standardized coefficients and the standardized weights were then multiplied to create a standardized coefficient that was weighted based on it's impact for Tobin's Q. These variables were added together for each firm to create a firm's score.

Once the score is calculated for each firm they were correlated against the over/undercompensating variable. This correlation was graphed for sizes each firm size. Additionally, we calculated the average performance score for each firm size, then created a correlation table between those average scores and the overcompensation variable for each of the four compensation cases.

