# Scheduling a Meeting

If you integrate a calendar tool for scheduling, the function might look like this:

```python

def schedule_meeting(date: str, time: str, participants: list):
    # A mock meeting scheduler
    return {"status": "Scheduled", "date": date, "time": time, "participants": participants}
```

You could ask:

`Prompt:` "Can you schedule a meeting on October 21st at 10 AM with John and Sarah?"

The AI detects this is a scheduling task and calls the function:

`Response:` "Your meeting with John and Sarah has been scheduled for October 21st at 10 AM."