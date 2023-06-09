# There Is Such A Thing As Free Lunch
# Final Project - FIN 377
## Authors
Rha Overstreet, Alex Romanowski, Tobey Bill, Anna Harvey

## Project Description
This project analyzes the relationship between firm performance and CEO/Board of Director Compensation. Our analysis includes companies from the S&P 500 separated into size categories based on market value. For each firm, we ran a Ridge regression to predict firm CEO/BOD over/under compensation percentages. After achieving this metric, we calculated a measure of firm performance using the coefficients of a linear regression as weights for each relevant variable. Once both over/under compensation and firm performance had been calculated for the firms in question, the two were correlated, plotted on a scatterplot, and then average firm performance was listed in comparison with the four cases of over/undercompensation.  

## Our Approach
1. Research determinants of CEO and BOD compensation for our regressions
2. Use selected determinants to predict CEO and BOD Total Compensation
3. Determine if the CEO or BOD is overpaid or underpaid
4. Determine the relationship between the above results and firm performance

## File Directory and Interactions
**Steps to emulate findings**
1. Run the creating_cleaning_df.ipynb file found in the cleaning folder.
    - This file will clean and shape the data frames necessary for future use. 


2. Run the adding_varsto_ceo.ipynb file found in the adding folder.
    - This file will add the power and prestige variables used in the regressions later in the repository


3. In the regression folder there are 5 files. The BOD_Optimization and CEO_Optimization files can be used to see our methodology to optimize our Ridge model. These files can also be used to substitute your own regression models.
    - The 3 files to run in order to get our results are the small, medium, and large.ipynb. These files use our Ridge parameters to output our results. 
    - The folder: Saved_dfs holds the regression predictions and the binned datasets.
    


4. In the results folder, run Firm_performance.ipynb first.
    - Run Correlation Creation next.


**Data folders and what they hold**
1. inputs
    - The inputs folder holds the uncleaned datasets that where pulled from WRDS.
    

2. outputs
    - This folder is where the cleaned and modified datasets are created.


3. Data descriptions
    - This folder holds html files that visualize the data and their interactions.
    - data_reports.ipynb is the file which can be used to re-create the EDA htmls.
    - Firm_data_descriptions.csv holds variable descriptions
    
 
4. The saved_dfs in 3_regression
    - This folder holds the prediction results used in the results files



**Report**
Our report folder holds our report and findings


## Link to project website
__**[Project Website](https://tobeybill.github.io/TISATAFL/)**__

## Link to project presentation
__**[Project Presentation](https://docs.google.com/presentation/d/1QPhR5E__vT7tgivGgNYfhnt1yjnprXjheywIWayoJI4/edit?usp=sharing)**__

## Citations
1.  Mustafa A. Dah, Melissa B. Frye, "Is board compensation excessive?", Journal of Corporate Finance, Volume 45, 2017, Pages 566-585, ISSN 0929-1199, https://doi.org/10.1016/j.jcorpfin.2017.06.001.
	(https://www.sciencedirect.com/science/article/pii/S0929119917303589)
2.  Ahmed Bouteska, Salma Mefteh-Wali, "The determinants of CEO compensation: new insights from United States", Journal of Applied Accounting Research, 23 June 2021, vol. ahead-of-print, pages 663-686, ISSN 09675426, https://www.emerald.com/insight/content/doi/10.1108/JAAR-08-2020-0176/full/html#abstract
3.  Cordeiro, James J., and Rajaram Veliyath. "Beyond Pay for Performance: A Panel Study of the Determinants of CEO Compensation." American Business Review, vol. 21, no. 1, 2003, pp. 56-66. ProQuest, https://www.proquest.com/scholarly-journals/beyond-pay-performance-panel-study-determinants/docview/216292921/se-2.Ivan E. Brick, Oded Palmon, John K. Wald,
4.  Ivan E. Brick, Oded Palmon, John K. Wald, "CEO compensation, director compensation, and firm performance: Evidence of cronyism?", Journal of Corporate Finance, Volume 12, Issue 3, 2006, Pages 403-423, ISSN 0929-1199, https://doi.org/10.1016/j.jcorpfin.2005.08.005. (https://www.sciencedirect.com/science/article/pii/S0929119905000738) 
Sigo, Marxia Oli, Determinants of Firm Performance: A Subjective Model (August 1, 2020). 14th Annual Conference of Financial Economics and Accounting, Forthcoming, Available at SSRN:  https://ssrn.com/abstract=3665334


## Packages
```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
import matplotlib.ticker as mtick
from sklearn.model_selection import train_test_split,GridSearchCV,KFold,cross_validate
from sklearn import set_config
from sklearn.pipeline import make_pipeline 
from sklearn.compose import ColumnTransformer, make_column_selector
from sklearn.preprocessing import StandardScaler, OneHotEncoder
from sklearn.impute import SimpleImputer
from sklearn.metrics import r2_score
from df_after_transform import df_after_transform
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression
from ydata_profiling import ProfileReport
import pandas_datareader as pdr  # to install: !pip install pandas_datareader
from datetime import datetime
from statsmodels.formula.api import ols as sm_ols
from statsmodels.iolib.summary2 import summary_col # nicer tables
from sklearn.calibration import CalibrationDisplay
from sklearn.metrics import ConfusionMatrixDisplay,DetCurveDisplay,PrecisionRecallDisplay,RocCurveDisplay,classification_report,r2_score
from df_after_transform import df_after_transform
from sklearn.pipeline import make_pipeline, Pipeline
from sklearn.preprocessing import OneHotEncoder, StandardScaler, LabelEncoder
from sklearn.linear_model import Lasso, Ridge
from sklearn.feature_selection import SelectKBest, f_classif, VarianceThreshold
import yfinance as yf
```
## Data Service
    - Wharton Research Data Services
### Databases
1. [Compustat accounting variables](https://wrds-www.wharton.upenn.edu/pages/get-data/compustat-capital-iq-standard-poors/compustat/north-america-daily/fundamentals-annual/)
1. Execucomp
	1. [Director Compensation](https://wrds-www.wharton.upenn.edu/pages/get-data/compustat-capital-iq-standard-poors/compustat/execucomp/director-compensation/)
	1. [CEO Compensation](https://wrds-www.wharton.upenn.edu/pages/get-data/compustat-capital-iq-standard-poors/compustat/execucomp/annual-compensation/)

---

# TISATAFL
--- 
![](https://media.giphy.com/media/3orieQOEvQJdEsnZy8/giphy.gif)
