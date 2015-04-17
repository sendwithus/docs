# Customers API

*NOTE* -- All parameters are mandatory unless otherwise noted.

## Get a Specific Customer

This call will retrieve a customer by a specified email.

GET `/customers/matt@sendwithus.com`

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

This call will perform an update if a customer already exists with the specified email.

POST `/customers`

#### Params:

- email       -- Email (key) of the customer
- data (optional)       -- Key/Value data for customer profile
- locale (optional)     -- Specify a locale for this customer

#### Sample Request:

```json
{
	"email": "matt@sendwithus.com",
	"data": {
		"first_name": "Matt",
		"city": "San Francisco"
	},
	"locale": "de-DE"
}
```

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
        "locale": "en-US",
        "groups": [
            "grp_1234",
            "grp_5678"
        ]
    }
}
```


## Delete a Customer

DELETE `/customers/(:email)`

#### Params:

*no params*

#### Sample Response:

```javascript
{
	"success": true,
    "status": "OK"
}
```


## Get Email Logs for a Customer

This call will retrieve email logs for a customer.

GET `/customers/matt@sendwithus.com/logs`

#### Sample Response:

```json
{
	"success": true,
    "status": "OK",
    "logs": [{
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
    }]
}
```


## Add Customer to a Group

POST `/customers/(:email)/groups(:group_id)`

#### Params:

*no params*

#### Sample Response:

```json
{
    "success": true,
    "status": "OK"
}
```

## Remove Customer from a Group

DELETE `/customers/(:email)/groups(:group_id)`

#### Params:

*no params*

#### Sample Response:

```json
{
    "success": true,
    "status": "OK"
}
```
