# Customer Groups API

*NOTE* -- All parameters are mandatory unless otherwise noted.

## Get all Customer Groups

This call will display the name and description of all groups in your account.

GET `/groups`

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "groups": [
        {
            "name": "group_name",
            "description": "a description of the group"
        }
    ]
}
```

## Create/Update a Customer Group

POST/PUT `/groups/(:group_name)`

### Params

- description (optional)    -- A description of the customer group

#### Sample Request:

```json
{
    "description": "a description of the group"
}
```

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "group": {
        "name": "group_name",
        "description": "a description of the group"
    }
}
```

## Delete a Customer Group

DELETE `/groups/(:group_name)`

#### Sample Response:

```json
{
    "success": True,
    "status": "OK"
}
```

## Add a Customer to a Group

POST `/groups/(:group_name)/add

### Params

- email  -- Email address of the customer you are adding.  Also accepts a list of email addresses (max 100 per call).  Note: the customer must already exist within your sendwithus account to be successfully added to the group.

#### Sample Request:

```json
{
    "email": "sample@customer.com"
}
```

```json
{
    "email": [
        "cust1@sample.com",
        "cust2@sample.com",
        "cust3@sample.com"
    ]
}
```

#### Sample Response:

```
{
    "success": True,
    "status": "OK",
    "group_name": "sample_group"
}
```

## Remove a Customer from a Group

POST `/groups/(:group_name)/remove

### Params

- email  -- Email address of the customer you are removing.  Also accepts a list of email addresses (max 100 per call).

#### Sample Request:

```json
{
    "email": "sample@customer.com"
}
```

```json
{
    "email": [
        "cust1@sample.com",
        "cust2@sample.com",
        "cust3@sample.com"
    ]
}
```

#### Sample Response:

```
{
    "success": True,
    "status": "OK",
    "group_name": "sample_group"
}
```
