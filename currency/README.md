## Currency Conversion

You might have a function that calls a currency exchange API:

## Prompt

`Prompt:`"How much is 100 USD in EUR?"

## Functions

### Python

```python

def convert_currency(amount: float, from_currency: str, to_currency: str):
    # Mock conversion rate
    conversion_rate = 1.1  # USD to EUR for example
    return amount * conversion_rate
```

## Response

The AI recognizes this is a task for currency conversion and calls convert_currency(100, 'USD', 'EUR'). The response might be:

`Response` "100 USD is approximately 110 EUR.