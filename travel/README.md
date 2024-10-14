# Travel Distance Calculation

Let's say you want to calculate the distance between two cities using a travel distance function:

python

def calculate_distance(city1: str, city2: str):
    # Example response from an external API
    return {"distance_miles": 300, "city1": city1, "city2": city2}

You can then ask:

`Prompt:` "What is the distance between Los Angeles and San Francisco?"

The AI will pass the cities to calculate_distance("Los Angeles", "San Francisco") and respond:

`Response:` "The distance between Los Angeles and San Francisco is approximately 300 miles."


# Travel Booking and Itinerary Planning

AI could automate booking flights, hotels, and creating an optimized travel itinerary based on user preferences and constraints.
Use Case:

## Prompt:

"Plan a 5-day trip to Paris starting from October 25th, book the cheapest direct flight, a 4-star hotel near the Eiffel Tower, and create a sightseeing itinerary for each day."

## Functions:

    search_flights(origin: str, destination: str, date: str, filters: dict): Finds flights based on the user’s preferences.
    book_hotel(location: str, stars: int, check_in: str, check_out: str): Books a hotel.
    generate_itinerary(city: str, days: int, interests: list): Creates a sightseeing itinerary based on user interests (e.g., museums, landmarks).

## Workflow:

    AI calls search_flights("New York", "Paris", "October 25th", {"direct": True, "cheapest": True}) to book a direct flight.
    It triggers book_hotel("Eiffel Tower, Paris", 4, "October 25th", "October 30th") to reserve a hotel room.
    Finally, it calls generate_itinerary("Paris", 5, ["museums", "landmarks", "restaurants"]) to provide a daily plan.

## Response:

"I’ve booked a direct flight to Paris for October 25th and a 4-star hotel near the Eiffel Tower. Here’s your 5-day itinerary, including visits to the Louvre and Notre-Dame."#