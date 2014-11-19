# Customers API

*NOTE* -- All parameters are mandatory unless otherwise noted.

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
		"city": "San Francisco",
		"nested_list": [1,2,3]
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
        "data": {...},
        "created": 5858858124 /* unix timestamp */
    }
}
```


## Delete a Customer

DELETE `/customers/(:email)`

#### Params:

*no params*

#### Sample Response:

```json
{
	"success": true,
    "status": "OK"
}
```
