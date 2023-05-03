## The Process:

Prior literature has individually examined the impact of Director compensation and CEO compensation on firm performance, but there are less studies that examine both variables together. Our research uses logistic regression to calculate an expected value for director and CEO compensation through their determinants while controlling for firm size and year. The expected value is then compared to the actual compensation to determine under or over compensation. These variables are used to create for different cases.

1)  CEOs and Directors are both overcompensated.
2)  CEOs and Directors are both undercompensated.
3)  CEO is overcompensated and Directors are undercompensated.
4)  CEO is undercompensated and Directors are overcompensated.

These four cases are then correlated to firm performance while controlling for determinants of firm performance.

# Methodology

## Director Compensation methodology and variables

### Variables
-Other Compensation
- Non Equity Incentives
- Cash Fees
- Stock Awards
- Option Awards
- Total Director Compensation
- Total Other Compensation
- Total Non Equity Incentives
       'noneq_incent', 'cash_fees', 'stock_awards', 'option_awards', 'spcode',
       'cusip', 'coname', 'year', 'total_director_comp', 'total_othcomp',
       'total_noneq_incent', 'total_cash_fees', 'total_stock_awards',
       'total_option_awards', 'mkvalt', 'size_category', 'signature_index',
       'liquidity', 'net_income', 'num_employees', 'market_value',
       'debt_to_equity', 'assets_in_place', 'capex_by_assets',
       'return_on_equity'
- Comp variables
- Determinants
- Regression while controlling firm size

Ceo comp:
- Comp variables
- Determinants
- Regression while controlling firm size

Overpayment:
- Predict after train
- Variable creation
- Case production

Correlation:
- Control variables
- Use of overpayment
