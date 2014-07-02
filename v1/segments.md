# Segments API

*NOTE* -- All parameters are mandatory unless otherwise noted.

## List all Segments

GET `/segments`

Sample Response

## Retrieve a Segment (Private Beta)

GET `/segments/(:segment_id)`

Sample Repsonse:

```json
        [
            {
                "object": "customer",
                "created": 1234567890,
                "email": "customer@email.com"
            }, {
                "object": "customer",
                "created": 1234567891,
                "email": "customer@email.com"
            }
        ]
```
##### NOTE: Segments returned by the API are currently limited to 500 customers max.

## Send to a Segment

POST `/segments/(:segment_id)/send`

Params:

- email_id       -- ID of the template to send
- email_data (optional)       -- Key/Value data to merge into template


