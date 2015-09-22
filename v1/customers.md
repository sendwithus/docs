---
title: Customers
type: api
order: 6
---

# Customers API

*NOTE* -- All parameters are mandatory unless otherwise noted.

## Get a Specific Customer

This call will retrieve a customer by a specified email.

`GET /customers/us@sendwithus.com`

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "customer": {
    "object": "customer",
        "email": "customer@example.com",
        "data": {
            "first_name": "Matt",
            "city": "San Francisco"
        },
        "created": 5858858124,
        "locale": "not set",
        "groups": [
            "grp_1234",
            "grp_5678"
        ]
    }
}
```

## Creating/Updating a New Customer

All parameters are mandatory unless otherwise noted.

If a Customer already exists with the specified email address, then a data merge is performed. Merge operations will:

* replace existing attributes with new values
* add any new attributes to the Customer

Merge operations will never remove attributes from a Customer. Note that customer data can only be simple data types like strings and integers.

`POST /customers`

#### Params:

- email       -- Email (key) of the customer
- data (optional)       -- Key/Value data for customer profile
- locale (optional)     -- Specify a locale for this customer
- groups (optional)     -- Will be added to the list of existing groups

#### Sample Request:

```json
{
    "email": "matt@sendwithus.com",
    "data": {
        "first_name": "Matt",
        "city": "San Francisco"
    },
    "locale": "de-DE",
    "groups": [
        "grp_djd1234950",
        "grp_jdkj497283"
    ]
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
- created_gt (optional)     -- A Unix Timestamp used as a index for the search. The logs retrieved will have been sent after timestamp specified or been scheduled for sending.

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


## Add Customer to a Group

`POST /customers/(:email)/groups/(:group_id)`

#### Sample Response:

```json
{
    "success": true,
    "status": "OK"
}
```

## Remove Customer from a Group

`DELETE /customers/(:email)/groups/(:group_id)`

#### Sample Response:

```json
{
    "success": true,
    "status": "OK"
}
```
