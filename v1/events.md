# Events API

**WARNING: This API is currently in private beta.**

If you have questions or would like early access, please [email us](mailto:us@sendwithus.com).

## Add Event to Customer

This will add a new event to a specific customer in your sendwithus account.

POST `/events`

Params:

- email       -- Email of the customer to add the event to
- event_name    -- Name of the event to record
- revenue (optional)   -- Revenue associated with this event, in cents.


Sample Request:

```json
{
    "email": "customer@yourdomain.com",
    "event_name": "purchase",
    "revenue": 1999
}
```

Sample Response:

```json
{
    "success": true,
    "status": "OK"
}
```
