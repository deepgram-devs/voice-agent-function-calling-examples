# Fetching Stock Prices

If you have a function to get stock prices from a financial data API, it could look like this:

```python

def get_stock_price(symbol: str):
    # Mock data for stock price
    return {"symbol": symbol, "price": 150.25}
```

You could ask:

`Prompt:` "What is the current price of Apple stock?"

The AI would call get_stock_price('AAPL') and respond:

`Response:` "The current price of Apple stock (AAPL) is $150.25."

---

# Real-Time Financial Portfolio Management

In this use case, the AI can retrieve real-time stock data, execute trades, and analyze portfolio performance for users who manage their investments.


## Prompt:

`Prompt:` "Review my investment portfolio and sell any stocks that have dropped more than 5% over the last month."

## Functions:

### Get Portfolio Data

This function simulates retrieving a user's investment portfolio. It returns a dictionary with the stocks and quantities the user owns (e.g., 50 shares of Apple).

```python
# Mock implementation of the get_portfolio_data function
def get_portfolio_data(user_id: str):
    # Simulate retrieving a user's investment portfolio
    portfolios = {
        "user123": {
            "AAPL": 50,  # 50 shares of Apple
            "GOOGL": 30, # 30 shares of Google
            "TSLA": 20   # 20 shares of Tesla
        },
        "user456": {
            "MSFT": 40,  # 40 shares of Microsoft
            "AMZN": 25   # 25 shares of Amazon
        }
    }
    return portfolios.get(user_id, "Portfolio not found for user ID.")
```

### Get Stock Performance

Fetches the performance of a specific stock over a given time period (e.g., 1 month or 3 months). The performance is provided as a percentage change.

```python
# Mock implementation of the get_stock_performance function
def get_stock_performance(stock_symbol: str, duration: str):
    # Simulate fetching stock performance data
    performance_data = {
        "AAPL": {"1 month": -6.5, "3 months": 4.2},   # -6.5% over the last month, +4.2% over 3 months
        "GOOGL": {"1 month": -2.3, "3 months": 7.8},
        "TSLA": {"1 month": 8.0, "3 months": 12.0},
        "MSFT": {"1 month": 3.5, "3 months": 9.1},
        "AMZN": {"1 month": -5.0, "3 months": 10.5}
    }
    stock_performance = performance_data.get(stock_symbol, {})
    return stock_performance.get(duration, "Performance data not available for this duration.")
```

### Sell Stock

Executes a trade to sell the specified quantity of a stock. It returns a message confirming the sale.

```python
# Mock implementation of the sell_stock function
def sell_stock(stock_symbol: str, quantity: int):
    # Simulate selling the stock
    if quantity <= 0:
        return "Invalid trade. Quantity must be greater than 0."

    return f"Executed trade: Sold {quantity} shares of {stock_symbol}."

# Example usage
user_id = "user123"
portfolio = get_portfolio_data(user_id)

if isinstance(portfolio, dict):
    print(f"Portfolio for {user_id}: {portfolio}")

    # Example: Checking stock performance and deciding to sell stocks
    for stock, quantity in portfolio.items():
        performance = get_stock_performance(stock, "1 month")
        print(f"Performance of {stock} over 1 month: {performance}%")

        # Example logic: Sell if performance over the past month is negative
        if isinstance(performance, (int, float)) and performance < -5:
            sell_confirmation = sell_stock(stock, quantity)
            print(sell_confirmation)
else:
    print(portfolio)
```


## Response:

`Response:` "I reviewed your portfolio and sold 50 shares of XYZ Corp, which dropped by 7% this month."


