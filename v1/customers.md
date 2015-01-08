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
        "created": 5858858124
    }
}
```

## Creating/Updating a New Customer

This call will perform an update if a customer already exists with the specified email.

POST `/customers`

#### Params:

- email       -- Email (key) of the customer
- data (optional)       -- Key/Value data for customer profile

#### Sample Request:

```json
{
	"email": "matt@sendwithus.com",
	"data": {
		"first_name": "Matt",
		"city": "San Francisco"
	}
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
        "created": 5858858124
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
