---
title: Batch API Requests
type: api
order: 12
---

# Batch API

The sendwithus batch endpoint enables multiple API calls
to be made in a single HTTP request.

*NOTE* -- Batch sizes over 100 requests are not recommended.


## Sample Batch (Multiple Sends)

`POST /batch`

#### Params:

- path -- API path to call
- method -- HTTP method to use
- body -- HTTP request body


#### Sample Request:

```json
[{
    "path": "/api/v1/send",
    "method": "POST",
    "body": {
        "email_id": "tem_QszsrasQP6nqGewZhKB2G",
        "recipient": {
            "address": "test+1@mydomain.com"
        }
    }
}, {
    "path": "/api/v1/send",
    "method": "POST",
    "body": {
        "email_id": "tem_doesntexist",
        "recipient": {
            "address": "test+2@mydomain.com"
        }
    }
}]
```


#### Sample Response:


*NOTE* -- Responses are returned in the same order as requested.

```json
[{
    "path": "/api/v1/send",
    "status_code": 200,
    "method": "POST",
    "body": {
        "success": true,
        "email": {
            "name": "Docs Page Curl Command",
            "version_name": "Original"
        },
        "receipt_id": "374s1700-279f-4642-b775-58e8231d443b-y6cem5",
        "status": "OK"
    }
}, {
    "path": "/api/v1/send",
    "status_code": 400,
    "method": "POST",
    "body": {
        "Invalid email_id, email not found"
    }
}]
```
