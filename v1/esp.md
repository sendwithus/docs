# sendwithus ESP Account API

The sendwithus ESP Accounts API allows for fetch and creation of ESP Accounts
for a given sendwithus account. **Note that the following specification is not
finalized and is subject to change.**


## List all ESP Accounts

GET `/esp_accounts`

#### Params:

- esp\_type (optional) -- Filter response to only return ESP accounts of a certain type
- count (optional) -- The number of logs to return. *Max: 100, Default: 100.*
- offset (optional) -- Offset the number of logs to return. *Default: 0*

#### Sample Response:

```json
[
    {
        "object": "esp_account",
        "id": "esp_asdf1234qwfpgj",
        "created": 1234567890,
        "esp_type": "sendgrid",
        "name": "My SendGrid Account"
    }
]
```

#### Possible esp_account.esp_type values:

- **sendgrid**
- **mailgun**
- **mandrill**
- **smtp**


## Add a new ESP Account.

POST `/esp_accounts`

#### Params:

- send\_test\_email (optional) -- Send a test email on successful configuration
                                to the owner(s) of the sendwithus account

#### Sample Request:

```json
{
    "name": "My SendGrid Subuser",
    "esp_type": "sendgrid",
    "credentials": {
        "username": "mysendgridusername",
        "password": "password123"
    }
}
```

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "esp_account": {
        "object": "esp_account",
        "id": "esp_asdf12rastrast",
        "created": 1234567890,
        "esp_type": "sendgrid",
        "name": "My SendGrid Subuser"
    }
}
```


## Set a given ESP Account as the default for sending emails.

PUT `/esp_accounts/set_default`

#### Sample Request:

```json
{
    "esp_id": "esp_asdf12rastrast"
}
```

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "esp_account": {
        "object": "esp_account",
        "id": "esp_asdf12rastrast",
        "created": 1234567890,
        "esp_type": "sendgrid",
        "name": "My SendGrid Subuser"
    }
}
```
