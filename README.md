# Quantitative Global - v1 API

This package allows access to data provided by [Quantitative Global Indices](https://qg-indices.com/).

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install quantglobal.

```bash
pip install quantglobal
```

## Usage

```python
import QuantGlobal as qg
data = qg.download(key, strategy, underlying, from_date, **end_date)
```
### Valid parameters
- key
  - the email address associated with your account (e.g., 'your_address@ email.com')
- strategy
  - 'dca' (Dual Class Arbitrage)
  - 'pt' (Pairs Trading)
  - 'pt_extended' (Pairs Trading w/ Extended Data)
- underlying
  - For Dual Class Arbitrage ('dca'), the valid underlying parameters are:
    - 'google','zillow','fox','news'
  - For Pairs Trading (both 'pt' and 'pt_extended'), the valid underlying parameters are:
    - 'communications','consumer_discretionary','consumer_staples','energy','financials','healthcare','industrials','basic_materials','technology','utilities'
- from_date / end_date (optional)
  - date in YYYY-mm-dd format
  
## Sample Request

```python
import QuantGlobal as qg
data = qg.download(key = 'authenticated_user@email.com', strategy = 'dca', underlying = 'google', from_date = '2022-11-30')
```
Output:
| datetime        | Cumulative Returns | GOOGL Cumulative Returns | Spread      | GOOG Intraday Performance | GOOGL Intraday Performance | Underperformer | Overperformer |
|-----------------|--------------------|--------------------------|-------------|---------------------------|----------------------------|----------------|---------------|
| 11/30/2022 9:30 | 100                | 100                      | 0           | 0.00%                     | 0.00%                      | GOOG           | GOOG          |
| 11/30/2022 9:31 | 99.78965082        | 99.75753742              | 0.032113397 | -0.21%                    | -0.24%                     | GOOGL          | GOOG          |
| 11/30/2022 9:32 | 99.73763733        | 99.70536385              | 0.016552133 | -0.26%                    | -0.29%                     | GOOGL          | GOOG          |
| 11/30/2022 9:33 | 100.2119105        | 100.2125374              | 0.01312691  | 0.21%                     | 0.21%                      | GOOG           | GOOGL         |
| 11/30/2022 9:34 | 100.2750597        | 100.3074711              | 0.025219918 | 0.28%                     | 0.31%                      | GOOG           | GOOGL         |
