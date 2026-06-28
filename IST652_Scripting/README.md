IST 652: Scripting for Data Analysis

**Project:** Stock Price Analysis & Forecasting
**Team:** Najah Bell, Derek Eodice, Rohan Madhur, Matthew Woods, Antonio Sanders, Denzel Thomas
**Tools:** Python · yfinance · pandas · NLTK · VADER · BeautifulSoup · statsmodels (ETS)



Project Overview

This project applied Python scripting to collect, preprocess, and analyze daily historical price data for the four major U.S. stock indices, then produced 30-day forecasts and performed sentiment analysis on financial news articles for each index.

**Indices analyzed:**
•	Dow Jones Industrial Average (^DJI)
•	Nasdaq Composite (^IXIC)
•	S&P 500 (^GSPC)
•	Russell 2000 (^RUT)



Data Collection

Live data was pulled from Yahoo Finance using the `yfinance` Python package. Variables collected: closing price, highest price, lowest price, opening price, and trading volume. The date window spanned January 1, 2020 to the current date, with the end date set dynamically using `date.today()` so the script always incorporates the most recent data.



Preprocessing

•	Verified no missing values or duplicated dates
•	Confirmed date index stored as proper datetime object
•	Validated price and volume fields in correct numeric types
•	For text data: scraped articles with BeautifulSoup, stripped HTML artifacts, normalized to lowercase



Forecasting Models Evaluated

| Model | Selected? | Reason |
|-------|-----------|--------|
| ARIMA | No | Requires manual parameter tuning |
| LSTM | No | High complexity, outside project scope |
| **ETS (Exponential Smoothing)** | **Yes** | Automatic trend/seasonality handling, interpretable, efficient |

**ETS configuration:** Additive trend, no seasonality

30-Day Forecast Results

| Index | Forecast | Projected Growth |
|-------|----------|-----------------|
| Dow Jones (^DJI) | 45,850 | +1.44% |
| Nasdaq (^IXIC) | 22,120 | +3.12% |
| S&P 500 (^GSPC) | 6,520 | +1.08% |
| Russell 2000 (^RUT) | 2,520 | +2.89% |

Russell 2000 showed the strongest relative upside, attributed to small-cap rotation dynamics.



Text Mining & Sentiment Analysis

One financial news article per index was analyzed using:
•	**BeautifulSoup** — web scraping and HTML cleaning
•	**NLTK** — tokenization and top-10 word frequency analysis
•	**VADER** — compound sentiment scoring

Sentiment scores aligned with actual market performance for 3 of 4 indices. The S&P 500 was misclassified as positive despite a clearly negative article — VADER overweighted terms like "strong" and "rally" even in negative contexts, a known limitation of general-purpose sentiment models applied to financial language.



Files in This Folder

| File | Description |
|------|-------------|
| `Group_Alpha_Stock_Analysis.docx` | Full project report |
| `Group_Alpha_Stock_Analysis.ipynb` | Python script  |



Ethical Reflection

VADER's misclassification of the S&P 500 article is not merely a technical error. Deployed in a production trading system without domain-specific validation, a model that systematically misreads negative financial sentiment as positive could generate recommendations with serious financial consequences. This reinforces the importance of model validation and epistemic humility when applying general-purpose NLP tools outside their intended domain.

