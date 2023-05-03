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

----- 

# Methodology

## Regression Analysis for Director and CEO Compensation

The regressions for director and CEO compensation were ran seperatley, but the overarching process is the same.

Through our research, we learned that firms of different sizes have varrying payout structures to their executives and directors. We split the firms into 3 different size categories to allow for individual treatment during the regressions. Small firms were catagorized with a maximum market cap at $10 billion, followed by medium at $200 billion, and large anything over $200 billion.

After splitting the firms in their respective bins, we ran a Ridge Regression 
on our determinates for compensation (Independent Variables) against director/CEO total compensation (Dependent 
variable). 

We used GridSearchCV to optimized each our models for the alpha and K value. After many iterations, the best_alpha function was used to pick the set of parameters that fit the data the best. 

# add code here!!!!

Despite optimizing, the director model was unable to fit the firms in the "huge" bin within any degree of accuracy. This suggests that different determinates govern director compensation at giant firms. If we were to re-run the analysis, we would do more research to find different determinates. For the time being, we decided to omit the data because no meaningful predications could be made.
 

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
- r2 result: -0.072973


__Ceo Results__

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

------

## Overpayment Predictions

Once we fit the models to the training data set, we used them to predict compensation for our holdout data. That provided us with a predicted compensation. We used this variable to create an overpayment variable.

Overpayment = Actual Pay / Predicted Pay

-----

## Firm Performance Score

We needed a measure of performance to determine the effects of compensation on firm performance. Initially, we were going to use Tobin's Q as our measure of performance. However, literature review done by Sigo prompted us to take the analysis one step further. Because the review outlines so many different factors that impact firm performance, we decided to run another regression that fit those determinates to the performance itself.

### Add regression here

The regression produced an r2 of ___ . Due to the significant r2 value, we were able to use the model to create a future firm performance score. The score was created by __ . Once the performance score was calculated, we ran a correlation between the performance score and the overpayment variable.
