Customers API
=============

*NOTE* -- All parameters are mandatory unless otherwise noted.

Creating a New Customer (Done)
-----------------------

POST `/customers`

Params:

- email       -- Email (key) of the customer
- data (opt)       -- Key/Value data for customer profile


Update a Customer (Done)
-------------------------------

PUT `/customers/(:email)`

Params:

- data       -- Key/Value data to update customer profile


Delete a Customer (Done)
---------------------------

DELETE `/customers/(:email)`

Params:

*no params*
