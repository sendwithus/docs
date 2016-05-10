---
title: Segments
type: api
order: 9
---

# Segments API

*NOTE* -- All parameters are mandatory unless otherwise noted.

## List all Segments

`GET /segments`

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

`POST /segments/(:segment_id)/send`

#### Params:

- email_id                      -- ID of the template to send
- email_data (optional)         -- Key/Value data to merge into template
- esp\_account (optional)       -- ID of the ESP Account to send emails through. ex: esp_1a2b3c4d

#### Sample Request

```json
{
    "email_id": "tem_ACdWZKZf4CtZNPM27WAdf6",
    "email_data": {
        "Weekly_Newsletter":
        [
            {
                "url": "http://www.example.com/1",
                "image": "http://www.example.com/image1.jpg",
                "text": "Check this sweet thing out!"
            },
            {
                "url": "http://www.example.com/2",
                "image": "http://www.example.com/image2.png",
                "text": "Check this other sweet thing out!"
            }
        ]
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
