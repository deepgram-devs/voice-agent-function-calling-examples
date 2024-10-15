# Automated Personal Assistant (Task Orchestration)

A personal assistant that can handle multiple related tasks, such as sending an email, setting up calendar events, and reserving a restaurant.`

## Prompt:

`Prompt:` "Schedule a lunch with Jane at a French restaurant next Tuesday at 1 PM, and send her an email invitation."

## Functions:

### Search Restaurants

 This function simulates searching for nearby restaurants that match the specified cuisine (e.g., "French") and location (e.g., "Main St") on a given date (e.g., "2024-10-24"). It checks availability based on mock data.

``` python
# Mock implementation of the search_restaurants function
def search_restaurants(cuisine: str, date: str, location: str):
    # Simulate searching for restaurants
    restaurant_data = {
        "French": [
            {"name": "Le Petit Bistro", "address": "123 Main St", "availability": ["2024-10-17", "2024-10-24"]},
            {"name": "Café de Paris", "address": "456 Elm St", "availability": ["2024-10-24", "2024-10-31"]}
        ],
        "Italian": [
            {"name": "Pasta House", "address": "789 Oak St", "availability": ["2024-10-20", "2024-10-24"]},
        ]
    }

    available_restaurants = []
    for restaurant in restaurant_data.get(cuisine, []):
        if date in restaurant["availability"] and location.lower() in restaurant["address"].lower():
            available_restaurants.append(restaurant)

    if available_restaurants:
        return f"Available {cuisine} restaurants on {date} in {location}:\n" + "\n".join(
            [f"{res['name']} at {res['address']}" for res in available_restaurants]
        )
    else:
        return f"No available {cuisine} restaurants found on {date} in {location}."
```

### Schedule Meeting

This function simulates scheduling a meeting on a specific date and time with a list of participants. It returns a confirmation message with the meeting details.

``` python

# Mock implementation of the schedule_meeting function
def schedule_meeting(date: str, time: str, participants: list):
    # Simulate scheduling a meeting
    if not participants:
        return "Meeting cannot be scheduled without participants."

    return f"Meeting scheduled on {date} at {time} with participants: {', '.join(participants)}."

```


### Send Email

This function simulates sending an email to a recipient with a subject and body. It returns a confirmation message once the email is sent.

```python

# Mock implementation of the send_email function
def send_email(to: str, subject: str, body: str):
    # Simulate sending an email
    return f"Email sent to {to} with subject '{subject}' and body:\n{body}"

# Example usage

# Example 1: Search for restaurants
cuisine = "French"
date = "2024-10-24"  # Next Tuesday in this example
location = "Main St"
restaurant_search_result = search_restaurants(cuisine, date, location)
print(restaurant_search_result)

# Example 2: Schedule a meeting
meeting_date = "2024-10-15"
meeting_time = "14:00"
participants = ["Alice", "Bob", "Charlie"]
meeting_status = schedule_meeting(meeting_date, meeting_time, participants)
print(meeting_status)

# Example 3: Send an email
email_to = "alice@example.com"
email_subject = "Meeting Invitation"
email_body = "You are invited to a meeting on October 15th at 2:00 PM with Bob and Charlie."
email_status = send_email(email_to, email_subject, email_body)
print(email_status)

```

## Workflow:

1. AI calls `search_restaurants("French", "next Tuesday", "local")` to find a suitable restaurant.
2. AI uses `schedule_meeting("next Tuesday", "1 PM", ["Jane"])` to create the event.
3. AI triggers `send_email("jane@example.com", "Lunch Invitation", "Let's meet for lunch at XYZ Restaurant next Tuesday at 1 PM.")`.

## Response:

`Response:` "I've booked a table at XYZ French Restaurant, scheduled lunch with Jane for next Tuesday at 1 PM, and sent her an invitation via email."