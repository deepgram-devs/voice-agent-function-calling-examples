# Fetching Weather Information

Suppose you want the AI to fetch current weather data from an external weather API, you could define a function like this:

```python
python

def get_weather(location: str):
    # Call an external weather API (this is a mock-up)
    return {"temperature": 72, "condition": "Sunny", "location": location}
```

You could then prompt the AI like this:

`Prompt:` "What is the current weather in San Francisco?"

The AI would detect that this requires weather information and trigger the get_weather function with "San Francisco" as the argument, returning a result like:

`Response:` "The current temperature in San Francisco is 72°F and the condition is Sunny."