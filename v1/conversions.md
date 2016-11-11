---
title: Conversions
type: api
order: 7
---

# Conversions API

**WARNING: This API is currently in beta.**

## Add Conversion to Customer

This will add a new conversion to a specific customer in your Sendwithus account.

`POST /customers/(:email)/conversions`

#### Params:

- revenue (optional)   -- Revenue associated with this conversion, in cents.
- timestamp (optional) -- Timestamp for the conversion time, in seconds.


#### Sample Request:

`POST /customers/greg@sendwithus.com/conversions`

```json
{
    "revenue": 1999
}
```

#### Sample Request with timestamp:

`POST /customers/greg@sendwithus.com/conversions`

```json
{
    "revenue": 1999,
    "timestamp": 1417321700
}
```

#### Sample Response:

```json
{
    "success": true,
    "status": "OK"
}
```
