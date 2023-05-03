# There Is Such A Thing As Free Lunch
# Final Project - FIN 377
## Authors
Rha Overstreet, Alex Romanowski, Tobey Bill, Anna Harvey

## Project Description
We are analyzing the relationship between firm performance and CEO/Board of Director Compensation. Our analysis includes companies from the S&P500, we then separated the firms based on market value. We then ran a Ridge regression to predict firm CEO/BOD over/under compensation. After predicting compensation we determined the relationship between compensation and firm performance. Firm performance was calculated using TobinsQ and a logistic regression to create a firm performance variable.

## Our Approach
1. Research determinants of CEO and BOD compensation for our regressions
2. Use selected determinants to predict CEO and BOD Total Compensation
3. Determine if the CEO or BOD is overpaid or underpaid
4. Determine relationship between above results and firm performance

## File Directory and Interactions


## Link to project website
tobeybill.github.io/TISATAFL/

## Citations
1.  Mustafa A. Dah, Melissa B. Frye, "Is board compensation excessive?", Journal of Corporate Finance, Volume 45, 2017, Pages 566-585, ISSN 0929-1199, https://doi.org/10.1016/j.jcorpfin.2017.06.001.
	(https://www.sciencedirect.com/science/article/pii/S0929119917303589)
2.  Ahmed Bouteska, Salma Mefteh-Wali, "The determinants of CEO compensation: new insights from United States", Journal of Applied Accounting Research, 23 June 2021, vol. ahead-of-print, pages 663-686, ISSN 09675426, https://www.emerald.com/insight/content/doi/10.1108/JAAR-08-2020-0176/full/html#abstract
3.  Cordeiro, James J., and Rajaram Veliyath. "Beyond Pay for Performance: A Panel Study of the Determinants of CEO Compensation." American Business Review, vol. 21, no. 1, 2003, pp. 56-66. ProQuest, https://www.proquest.com/scholarly-journals/beyond-pay-performance-panel-study-determinants/docview/216292921/se-2.Ivan E. Brick, Oded Palmon, John K. Wald,
4.  Ivan E. Brick, Oded Palmon, John K. Wald, "CEO compensation, director compensation, and firm performance: Evidence of cronyism?", Journal of Corporate Finance, Volume 12, Issue 3, 2006, Pages 403-423, ISSN 0929-1199, https://doi.org/10.1016/j.jcorpfin.2005.08.005. (https://www.sciencedirect.com/science/article/pii/S0929119905000738) 
Sigo, Marxia Oli, Determinants of Firm Performance: A Subjective Model (August 1, 2020). 14th Annual Conference of Financial Economics and Accounting, Forthcoming, Available at SSRN:  https://ssrn.com/abstract=3665334


## Packages
```import pandas as pd
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
import pandas as pd
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
set_config(display="diagram")
```
## Data Service
    - Wharton Research Data Services
### Databases
    - Compustat
    - Execucomp
    - Center for Research and Security Prices (CRSP)



# TISATAFL

__save all excel to csv__

![image](https://user-images.githubusercontent.com/60451986/235734159-b962da12-2e8c-4f6c-bd66-ca2751948c95.png)


# _Updates and Changes_

__Needed Data and it's uses__

![image](https://user-images.githubusercontent.com/60451986/234738772-d35de719-3860-45bc-ac64-5e9626d31cad.png)

https://www.sciencedirect.com/science/article/pii/S0929119917303589#s0010![image](https://user-images.githubusercontent.com/60451986/234755851-d3bd5a91-10a1-42eb-89e4-16c7a64967fc.png)

![image](https://user-images.githubusercontent.com/60451986/234755821-f8b697b7-665e-4492-868e-40b43c5c646e.png)


![image](https://user-images.githubusercontent.com/60451986/234976098-c8c55f02-f672-45de-b2ee-a51ec801ea4b.png)


link at the top of the image https://www.emerald.com/insight/content/doi/10.1108/JAAR-08-2020-0176/full/html#sec004![image](https://user-images.githubusercontent.com/60451986/234976159-3ae10640-3c8c-46e3-a580-09ae28e38c9b.png)



link at the bottom of the image https://www.emerald.com/insight/content/doi/10.1108/JAAR-08-2020-0176/full/html#sec004![image](https://user-images.githubusercontent.com/60451986/234976200-cfdd364e-7d0d-4e6f-bbf7-ae010362ad9e.png)

__Control Variables for firms__

We do not need all 46, grab as many as is convenient and are not repeats. This is from a paper written about Indian Companies but it's close enough.

here's the link for this
https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3665334

![image](https://user-images.githubusercontent.com/60451986/235383012-bee5c246-81f9-4ccb-8012-78b03f228773.png)



![image](https://user-images.githubusercontent.com/60451986/235374611-b8035dfe-3b28-475e-8a0b-7e64198b0a63.png)



# __Initial Proposal__

General idea: The question/problem are you interested in, the data you need to acquire, the variables you’ll use, and the plan for how you’ll analyze it (what methods you’ll try and why you think they apply to your problem), considerations about how data might impact that.

Treat this document as if it is public facing, and a proposal for which you would like funding. That is, the proposal document should be polished (both in visual formatting and editing) for external audiences.

Graded on: question viability, creativity, finance application, plan sketch, writing quality.

Instructions for the proposals are here.


# __Final Proposal__

I will provide feedback on your proposals to help you “right size” your goal and avoid some potholes.

Graded on: The improvement from the prior version, how feedback was incorporated, and quality after revisions


# __Project Status Report__

General idea: You’ve now acquired the key data and finished most of the data cleaning.

Purpose: Needs to show progress and that you’re on track!

Ideal deliverable: A notebook file with nice data sections describing data source(s) and how you got/cleaned the data. This section could go straight into your final report if it’s polished enough.

Actual deliverable A notebook file that

describes (short bullet points) your data sources,

outlines (numbered list, broad steps, not minutia) how you acquired the data (for many groups, the downloading is in a separate file), got the data into python, and if you found any issues with the data you cleaned up (again, possibly a different file)

includes a bullet point list of the main observations from your EDA

shows your exploratory data analysis (EDA) (tables and figures and whatnot, does not need to be pretty or formatted)

Graded on: Data you have, EDA shown and discussed

**To DO**
- Data
  - Done by Anna
    - get code for S&P 500 tickers and GVKEY
    - make space seperated data
    - add in sector
  - Alex
    - get BOD comp data (ask rha if this is in the existing data)
  - aquire
    - how did we get the data (write up)
  - clean
    - clean data (coding)
    - summarize how the data is cleaned (write up)
    - summarize what issues were found (write up and code)
  - EDA and document
    - include graphics (write up and code)

**psuedo code for data file**

# __Repot at Submission__

On the due date (listed in the schedule), your repo should be cleaned and polished for publication. That means it should be cleaned of excess and random files, and that folders are sensible (data, temporary, code), the readme helps me/the TA/future visitors explore your repo easily. Your folder structure is up to you and will respond to the nature of your particular project, but I should be able to easily find

The readme should contain a link to the website built off this analysis

The code used to scrape and download data (and if you click-and-download anything, a link to the source) can be separate files, and the code used to load, clean, merge, and explore the data.

The code used to do the analysis

Your presentation file needs to be in this repo. If you use google slides, you should include them as a PDF in this folder / put a link to the slides in the readme.

Graded on: Folder org, read me, code readability/structure

Obvious caveats for grading: Form matters, check grammar, and cite work you build on. Plagiarism is not acceptable.*

**To do**
- data scraping and cleaning file
  - done by project status report
- analysis file
  - run regression on all data
  - save in csv
- report file
  - hypothesis
  - Data: tie in data cleaning file (done earlier)
  - Results:
    - create graphs from analysis file
  - conclusion:
    - these should be easy
- presentation file
  - save graphs from report file to jpeg
  - follow structure of report
  - convert powerpoint to pdf and link in readme
- readme
  - clear, makes sense

**psuedo code for analysis file**

**psuedo code for analysis file**

# __Website Dashboard__

We will talk about this more later.

Obvious caveats for grading: Form matters, check grammar, and cite work you build on. Plagiarism is not acceptable.*


# __presentation Slides__

I’ll discuss scheduling later.

You have 15 minutes

Everyone should contribute

There will be Q&A (from myself)

Teach your classmates and me something! Strive for clarity and try to make something about it memorable.

Method: You can present a powerpoint, a jupyter file, or jupyter slides (nice!). I’ll leave it up to your group to present in the manner you consider most effective for your project.

Time: Each group will have up to 15 minutes to present your project, so build your presentation file accordingly. Try to avoid “speed talking” to make the time work. Less is more, usually. Sadly, 15 minutes won’t be enough to show everything you did, so focus on big picture details rather than on the syntax of line 89 of your code.

Content: A presentation’s structure is tailored even more to its material than a report is, so what your slides show is up to you. Be creative, and have fun. Try to convey to me and your peers why the question is interesting, describe plainly your approach and why your approach makes sense, what your main analytical findings are, and what you concluded from the exercise. You can even show/use your website during your presentation if you want.

Enjoyment: Don’t be afraid to “market yourselves”! If you did something impressive (tons and tons of data, or an impressive scraper, or a great model), find a way to tastefully show your classmates (and me) the cool stuff you did!

Obvious caveats for grading: Form matters, check grammar, and cite work you build on. Plagiarism is not acceptable.*
