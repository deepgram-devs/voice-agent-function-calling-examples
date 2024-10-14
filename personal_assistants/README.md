# Automated Personal Assistant (Task Orchestration)

A personal assistant that can handle multiple related tasks, such as sending an email, setting up calendar events, and reserving a restaurant.
Use Case:

## Prompt:

"Schedule a lunch with Sarah at a French restaurant next Tuesday at 1 PM, and send her an email invitation."

## Functions:

    search_restaurants(cuisine: str, date: str, location: str): Searches for nearby French restaurants available next Tuesday.
    schedule_meeting(date: str, time: str, participants: list): Adds a meeting to the calendar.
    send_email(to: str, subject: str, body: str): Sends an email invitation.

## Workflow:

    AI calls search_restaurants("French", "next Tuesday", "local") to find a suitable restaurant.
    AI uses schedule_meeting("next Tuesday", "1 PM", ["Sarah"]) to create the event.
    AI triggers send_email("sarah@example.com", "Lunch Invitation", "Let's meet for lunch at XYZ Restaurant next Tuesday at 1 PM.").

## Response:

Response: "I've booked a table at XYZ French Restaurant, scheduled lunch with Sarah for next Tuesday at 1 PM, and sent her an invitation via email."