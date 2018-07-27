---
title: Customers
type: api
order: 6
---

# Customers API

*NOTE* -- All parameters are mandatory unless otherwise noted.

## Get a Specific Customer

This call will retrieve a customer by a specified email.

`GET /customers/customer@example.com`

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "customer": {
        "object": "customer",
        "email": "customer@example.com",
        "created": 5858858124,
        "locale": "en-US"
    }
}
```

## Creating/Updating a New Customer

All parameters are mandatory unless otherwise noted.

`POST /customers`

#### Params:

- email                 -- Email (key) of the customer
- locale (optional)     -- Specify a locale for this customer

#### Sample Request:

```json
{
    "email": "matt@sendwithus.com",
    "locale": "de-DE"
}
```

#### Sample Response:

```json
{
    "success": true,
    "status": "OK"
}
```


## Delete a Customer

`DELETE /customers/(:email)`

*NOTE* -- Deleting customers **will not** remove any pending scheduled drip campaign emails. To prevent these emails from being delivered, you must deactivate the user using the [Drip Campaign Deactivation endpoint](https://support.sendwithus.com/api/#deactivateacustomerfromallcampaigns).

#### Sample Response:

```javascript
{
    "success": true,
    "status": "OK"
}
```


## Get Email Logs for a Customer

This call will retrieve email logs for a customer.

`GET /customers/matt@sendwithus.com/logs?count={count}&created_lt={timestamp}&created_gt={timestamp}`

#### Arguments:

- count (optional)       -- A number between 1 and 100 to specify the number of logs returned (including scheduled drips). If none is specified, a limit of 100 sent logs is automatically imposed.
- created_lt (optional)       -- A Unix Timestamp used as a index for the search. The logs retrieved will have been sent before the timestamp specified.
- created_gt (optional)     -- A Unix Timestamp used as a index for the search. The logs retrieved will have been sent after the timestamp specified.

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "logs": [
        {
            "object": "log",
            "id": "log_asdf1234qwerty",
            "created": 1234567890,
            "recipient_name": "Matt",
            "recipient_address": "matt@sendwithus.com",
            "status": "opened",
            "message": "SendGrid: Message has been opened",
            "email_id": "tem_as8dfjha8dap",
            "email_name": "Order Confirmation",
            "email_version": "Version A"
        },
        { ... },
        { ... }
    ]
}
```
