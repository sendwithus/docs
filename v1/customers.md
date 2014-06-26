# Customers API

*NOTE* -- All parameters are mandatory unless otherwise noted.

## Creating/Updating a New Customer

This call will perform an update if a customer already exists with the specified email.

POST `/customers`

Params:

- email       -- Email (key) of the customer
- data (optional)       -- Key/Value data for customer profile


## Delete a Customer

DELETE `/customers/(:email)`

Params:

*no params*
