# Conversions API

**WARNING: This API is currently in beta.**

## Add Conversion to Customer

This will add a new conversion to a specific customer in your sendwithus account.

POST `/customers/[EMAIL_ADDRESS]/conversions`

Params:

- revenue (optional)   -- Revenue associated with this event, in cents.


Sample Request:

POST `/customers/greg@sendwithus.com/conversions`

```json
{
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