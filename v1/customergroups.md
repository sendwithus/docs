# Customer Groups API

*NOTE* -- All parameters are mandatory unless otherwise noted.

## Get all Customer Groups

This call will display the name and description of all groups in your account.

`GET /groups`

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "groups": [
        {
            "id": "grp_1234",
            "name": "group_name",
            "description": "a description of the group"
        }
    ]
}
```

## Create a Customer Group

`POST /groups`

### Params

- name    -- The name of the new group
- description (optional)    -- A description of the customer group

#### Sample Request:

```json
{
    "name": "new_group",
    "description": "a description of the group"
}
```

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "group": {
        "id": "grp_1234",
        "name": "new_group",
        "description": "a description of the group"
    }
}
```

## Update a Customer Group

`PUT /groups/(:group_id)`

### Params

- name (optional)           -- The new name for this group
- description (optional)    -- The new description of this group

#### Sample Request:

```json
{
    "name": "new_name",
    "description": "a description of the group"
}
```

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "group": {
        "id": "grp_1234",
        "name": "group_name",
        "description": "a description of the group"
    }
}
```

## Delete a Customer Group

`DELETE /groups/(:group_id)`

#### Sample Response:

```json
{
    "success": true,
    "status": "OK"
}
```
