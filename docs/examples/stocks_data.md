# Pandas

## Stock Data

Here’s a step-by-step guide with Python code to scrape the **S&P 500 stocks** from Wikipedia and use the `yfinance` library to retrieve stock information, historical data, financial statements, holders, and dividend activity.

---

### **1. Get S&P 500 Stocks from Wikipedia**

**Library**: Use `pandas` for scraping the table.

```python
import pandas as pd

def get_sp500_stocks():
    url = "https://en.wikipedia.org/wiki/List_of_S%26P_500_companies"
    tables = pd.read_html(url)
    sp500_table = tables[0]  # First table contains the S&P 500 data
    return sp500_table[['Symbol', 'Security']]  # Return only ticker and company name

# Example Usage
sp500_stocks = get_sp500_stocks()
print(sp500_stocks.head())
```

---

### **2. Get Historical Data Using `yfinance`**

**Library**: Use `yfinance` to fetch historical data.

```python
import yfinance as yf

def get_historical_data(tickers, start_date='2020-01-01', end_date='2024-01-01'):
    historical_data = {}
    for ticker in tickers:
        stock = yf.Ticker(ticker)
        data = stock.history(start=start_date, end=end_date)
        historical_data[ticker] = data
    return historical_data

# Example Usage: Get historical data for the top 5 stocks by market cap
top_tickers = sp500_stocks['Symbol'].head(5).tolist()
historical_data = get_historical_data(top_tickers)
for ticker, data in historical_data.items():
    print(f"Historical data for {ticker}:")
    print(data.head())
```

---

### **3. Get Stock Info**

Use `info` from `yfinance`.

```python
def get_stock_info(ticker):
    stock = yf.Ticker(ticker)
    return stock.info  # Returns a dictionary with stock information

# Example Usage
ticker = 'AAPL'  # Replace with any ticker
info = get_stock_info(ticker)
print(f"Stock Info for {ticker}:")
print(info)
```

---

### **4. Get Financial Statements**

Fetch annual and quarterly financials like income statements, cash flow, and balance sheets.

```python
def get_financial_statements(ticker):
    stock = yf.Ticker(ticker)
    return {
        'annual_income_statement': stock.financials,
        'quarterly_income_statement': stock.quarterly_financials,
        'annual_balance_sheet': stock.balance_sheet,
        'quarterly_balance_sheet': stock.quarterly_balance_sheet,
        'annual_cash_flow': stock.cashflow,
        'quarterly_cash_flow': stock.quarterly_cashflow,
    }

# Example Usage
ticker = 'AAPL'
financials = get_financial_statements(ticker)
print(f"Annual Income Statement for {ticker}:")
print(financials['annual_income_statement'])
```

---

### **5. Get Holders (Institutional and Insider)**

Retrieve holder information.

```python
def get_holders(ticker):
    stock = yf.Ticker(ticker)
    return {
        'institutional_holders': stock.institutional_holders,
        'major_holders': stock.major_holders,
        'insider_holders': stock.insider_holders
    }

# Example Usage
ticker = 'AAPL'
holders = get_holders(ticker)
print(f"Institutional Holders for {ticker}:")
print(holders['institutional_holders'])
```

---

### **6. Get Dividend Activity**

Extract dividend data.

```python
def get_dividend_activity(ticker):
    stock = yf.Ticker(ticker)
    dividends = stock.dividends
    if dividends.empty:
        return f"No dividend data for {ticker}."
    return dividends

# Example Usage
ticker = 'AAPL'
dividends = get_dividend_activity(ticker)
print(f"Dividend Activity for {ticker}:")
print(dividends)
```

---

### **7. Summary Script to Combine All Functions**

Here’s how to tie everything together:

```python
def get_stock_data(ticker):
    return {
        'info': get_stock_info(ticker),
        'historical_data': get_historical_data([ticker]),
        'financial_statements': get_financial_statements(ticker),
        'holders': get_holders(ticker),
        'dividends': get_dividend_activity(ticker),
    }

# Example Usage
ticker = 'AAPL'
stock_data = get_stock_data(ticker)
print(f"Full data for {ticker}:")
print(stock_data)
```

---

### **Required Libraries**

Install the necessary libraries:

```bash
pip install pandas yfinance lxml
```

This script covers fetching:

1. **S&P 500 tickers** from Wikipedia.
2. **Historical data** for selected stocks.
3. **Info, financials, holders, and dividends** for a single ticker or a batch of tickers.

Let me know if you’d like enhancements or detailed handling for any specific section!
