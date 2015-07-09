---
title: Logs
type: api
order: 2
---

# Logs API


*NOTE* -- All parameters are mandatory unless otherwise noted.

## Get a List all Logs

`GET /logs`

Retrieve a list of available logs. Logs are sorted in reverse chronological order.

#### Params:

- count (optional) -- The number of logs to return. *Max: 100, Default: 100.*
- offset (optional) -- Offset the number of logs to return. *Default: 0*
- created_gt (optional) -- Return logs created strictly after the given Unix Timestamp.
- created_gte (optional) -- Return logs created on or after the given Unix Timestamp.
- created_lt (optional) -- Return logs created strictly before the given Unix Timestamp.
- created_lte (optional) -- Return logs created on or before the given Unix Timestamp.

#### Sample Response:

```json
[
    {
        "object": "log",
        "id": "log_asdf1234qwerty",
        "created": 1234567890,
        "recipient_name": "Brad",
        "recipient_address": "brad@email.com",
        "status": "opened",
        "message": "SendGrid: Message has been opened",
        "email_id": "as8dfjha8dap",
        "email_name": "Order Confirmation",
        "email_version": "Version A"
    }
]
```

#### Possible log.status values:

- **requested**: sendwithus API request received
- **triggered**: email triggered by internal event, ie**: drip campaign**
- **queued**: email is queued for delivery
- **sent**: email has successfully reached email service provider
- **clicked**: a link in the email has been clicked
- **re_clicked**: a link in the email has been clicked more than once
- **opened**: the email has been opened
- **re_opened**: the email has been opened more than once
- **failed\_to\_queue**: an internal error has temporarily prevented delivery
- **failed\_to\_send**: an email service provider error has temporarily prevented delivery
- **processed**: email service provider has acknowledged delivery request
- **dropped**: email service provider has prevented email delivery
- **delivered**: email was successfully delivered to recipient
- **deferred**: email service provider has delayed email delivery
- **bounced**: email service provider could not deliver to recipient
- **reported\_as\_spam**: recipient has reported the email as spam
- **unsubscribed**: recipient has requested to be unsubscribed from this email



## Get a specific log + metadata

`GET /logs/(:log_id)`

A single Log object with all its details

#### Params:

- log_id -- String id of the Log to retrieve.

#### Sample Response:

```json
{
    "object": "log",
    "id": "log_asdf1234qwerty",
    "created": 1234567890,
    "recipient_name": "Brad",
    "recipient_address": "brad@email.com",
    "status": "opened",
    "message": "SendGrid: Message has been opened",
    "email_id": "as8dfjha8dap",
    "email_name": "Order Confirmation",
    "email_version": "Version A"
}
```

## Retrieve events for a specific log\_id.

`GET /logs/(:log_id)/events`

Return a list of all events associated with a given Log.

#### Params:

- log\_id (required) -- String id of the Log to retrieve events for.

#### Sample Response:

```json
[
    {
        "object": "event",
        "created": 1234567890,
        "type": "requested",
        "message": "requested"
    },
    {
        "object": "event",
        "created": 1234567891,
        "type": "queued",
        "message": "email queued"
    },
    {
        "object": "event",
        "created": 1234567892,
        "type": "failed_to_send",
        "message": "email failed to send, will retry"
    },
    {
        "object": "event",
        "created": 1234567893,
        "type": "sent",
        "message": "email sent through SendGrid"
    },
    {
        "object": "event",
        "created": 1234567894,
        "type": "opened",
        "message": "SendGrid: Email has been opened"
    },
    {
        "object": "event",
        "created": 1234567895,
        "type": "clicked",
        "message": "SendGrid: Link in email has been clicked"
    }
]
```


### Resend an existing Log

`POST /resend`

Resend a specific email by id.


#### Sample Request:

```json
{
    "log_id": "log_asdf123456qwerty"
}
```

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "log_id": "log_asdf123456qwerty",
    "email": {
        "name": "Order Confirmation",
        "version_name": "Version A"
    }
}
```
