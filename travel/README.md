# Travel Distance Calculation

Let's say you want to calculate the distance between two cities using a travel distance function:

```python

def calculate_distance(city1: str, city2: str):
    # Example response from an external API
    return {"distance_miles": 300, "city1": city1, "city2": city2}
```

You can then ask:

`Prompt:` "What is the distance between Los Angeles and San Francisco?"

The AI will pass the cities to calculate_distance("Los Angeles", "San Francisco") and respond:

`Response:` "The distance between Los Angeles and San Francisco is approximately 300 miles."

---

# Travel Booking and Itinerary Planning

AI could automate booking flights, hotels, and creating an optimized travel itinerary based on user preferences and constraints.
Use Case:

## Prompt:

`Prompt:` "Plan a 5-day trip to Paris starting from October 25th, book the cheapest direct flight, a 4-star hotel near the Eiffel Tower, and create a sightseeing itinerary for each day."

## Functions:

### Search Flights

This function simulates searching for flights based on origin, destination, and date. It applies user-defined filters such as maximum price and preferred airline and returns available flights that match the criteria.

```python
# Mock implementation of the search_flights function
def search_flights(origin: str, destination: str, date: str, filters: dict):
    # Simulate searching for flights based on origin, destination, date, and filters
    flights = [
        {"flight": "Flight 101", "origin": "NYC", "destination": "LAX", "date": "2024-10-20", "price": 300, "airline": "Delta", "duration": "6h"},
        {"flight": "Flight 202", "origin": "NYC", "destination": "LAX", "date": "2024-10-20", "price": 280, "airline": "United", "duration": "5.5h"},
        {"flight": "Flight 303", "origin": "NYC", "destination": "LAX", "date": "2024-10-20", "price": 350, "airline": "American", "duration": "6.5h"}
    ]

    # Apply filters (e.g., max price, preferred airline)
    filtered_flights = []
    for flight in flights:
        if flight["origin"] == origin and flight["destination"] == destination and flight["date"] == date:
            if "max_price" in filters and flight["price"] > filters["max_price"]:
                continue
            if "preferred_airline" in filters and flight["airline"] != filters["preferred_airline"]:
                continue
            filtered_flights.append(flight)

    if filtered_flights:
        return f"Available flights from {origin} to {destination} on {date}:\n" + "\n".join(
            [f"{flight['flight']} by {flight['airline']} - ${flight['price']}, {flight['duration']}" for flight in filtered_flights]
        )
    else:
        return "No flights found matching the criteria."

```

### Book Hotel

This function simulates booking a hotel in a specific location with a certain star rating for the check-in and check-out dates. It returns a confirmation if an available hotel is found

```python
# Mock implementation of the book_hotel function
def book_hotel(location: str, stars: int, check_in: str, check_out: str):
    # Simulate hotel booking based on location, star rating, and check-in/out dates
    hotels = [
        {"name": "Grand Plaza", "location": "New York", "stars": 5, "available": True},
        {"name": "City Hotel", "location": "New York", "stars": 4, "available": True},
        {"name": "Budget Inn", "location": "New York", "stars": 3, "available": False}
    ]

    for hotel in hotels:
        if hotel["location"].lower() == location.lower() and hotel["stars"] == stars and hotel["available"]:
            return f"Hotel '{hotel['name']}' booked in {location} from {check_in} to {check_out}."

    return f"No available {stars}-star hotels found in {location} for the requested dates."
```


### Generate Itinerary

This function generates a sightseeing itinerary for a city based on the number of days and user interests (e.g., museums, landmarks). It limits the number of attractions based on the available days.

```python
# Mock implementation of the generate_itinerary function
def generate_itinerary(city: str, days: int, interests: list):
    # Simulate generating a sightseeing itinerary based on city, days, and user interests
    attractions = {
        "museums": ["National History Museum", "Art Gallery", "Science Museum"],
        "landmarks": ["Central Park", "Statue of Liberty", "Empire State Building"],
        "parks": ["Botanical Garden", "City Park"],
        "shopping": ["5th Avenue", "Soho District"]
    }

    itinerary = []
    for interest in interests:
        if interest.lower() in attractions:
            itinerary.extend(attractions[interest.lower()][:days])  # Limit number of attractions to days available

    if itinerary:
        return f"Itinerary for {days} days in {city}:\n" + "\n".join(itinerary)
    else:
        return f"No attractions found for the interests specified in {city}."

# Example usage

# Example 1: Search for flights
origin = "NYC"
destination = "LAX"
flight_date = "2024-10-20"
filters = {"max_price": 320, "preferred_airline": "Delta"}
flight_search_result = search_flights(origin, destination, flight_date, filters)
print(flight_search_result)

# Example 2: Book a hotel
hotel_location = "New York"
stars = 5
check_in = "2024-11-01"
check_out = "2024-11-05"
hotel_booking_result = book_hotel(hotel_location, stars, check_in, check_out)
print(hotel_booking_result)

# Example 3: Generate a sightseeing itinerary
city = "New York"
days = 3
interests = ["museums", "landmarks"]
itinerary_result = generate_itinerary(city, days, interests)
print(itinerary_result)
```

## Workflow:

1. AI calls search_flights("New York", "Paris", "October 25th", {"direct": True, "cheapest": True}) to book a direct flight.
2. It triggers book_hotel("Eiffel Tower, Paris", 4, "October 25th", "October 30th") to reserve a hotel room.
3. Finally, it calls generate_itinerary("Paris", 5, ["museums", "landmarks", "restaurants"]) to provide a daily plan.

## Response:

`Prompt:` "I’ve booked a direct flight to Paris for October 25th and a 4-star hotel near the Eiffel Tower. Here’s your 5-day itinerary, including visits to the Louvre and Notre-Dame."#