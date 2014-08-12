# Events API

**WARNING: This API is currently in private beta.**

If you have questions or would like early access, please [email us](mailto:us@sendwithus.com).

## Add Event to Customer

This will add a new event to a specific customer in your sendwithus account.

POST `/customers/[EMAIL_ADDRESS]/events`

Params:

- event_name    -- Name of the event to record
- revenue (optional)   -- Revenue associated with this event, in cents.


Sample Request:

POST `/customers/greg@sendwithus.com/events`

```json
{
    "event_name": "purchase",
    "revenue": 1999
}
```

Sample Response:

STATUS CODE `200`
```json
{
    "success": true,
    "status": "OK"
}
```
