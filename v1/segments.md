# Segments API

*NOTE* -- All parameters are mandatory unless otherwise noted.

## List all Segments

GET `/segments`

#### Sample Response:

```json
[
    {
        "object": "segment",
        "created": 1404068087,
        "id": "seg_ksnfG9yTcRjbLpqCA9U",
        "name": "An Example Segment"
    }, {
        "object": "segment",
        "created": 1404068533,
        "id": "seg_jbLpqCA9UtykksnfG9y",
        "name": "A Second Example Segment"
    }, ...
]
```

## Send to a Segment

POST `/segments/(:segment_id)/send`

#### Params:

- email_id       -- ID of the template to send
- email_data (optional)       -- Key/Value data to merge into template

#### Sample Request

```json
{
    "email_id": "tem_ACdWZKZf4CtZNPM27WAdf6",
    "email_data": {
        "name": "John Doe"
    }
}
```

#### Sample Response

```json
{
    "status": "OK",
    "success": true
}
```

## Retrieve Customers in a Segment _(Beta Only)_

GET `/segments/(:segment_id)/run`

#### Sample Response:

```json
[
    {
        "object": "customer",
        "created": 1234567890,
        "email": "one@email.com"
    }, {
        "object": "customer",
        "created": 1234567891,
        "email": "two@email.com"
    }, ...
]
```

_NOTE: Please contact [beta@sendwithus.com](mailto:beta@sendwithus.com) to enable this endpoint for your account._
