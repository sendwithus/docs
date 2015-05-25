---
title: Email Service Providers
type: api
order: 5
---

# ESP Account API

The sendwithus ESP Accounts API allows for fetch and creation of ESP Accounts
for a given sendwithus account.

## List all ESP Accounts

`GET /esp_accounts`

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

#### Possible esp\_account.esp\_type values:

- **sendgrid**
- **mailgun**
- **mandrill**
- **postmark**
- **messagebus**
- **ses**
- **mailjet**
- **dyn**
- **sparkpost**
- **smtp**



## Add a new ESP Account.

`POST /esp_accounts`

#### Params:

- name -- Friendly name of the new esp account
- esp_type -- Must be one of the options listed above
- credentials -- Account credentials of the new esp account (must be in the format given below)
- send\_test\_email (optional) -- Send a test email on successful configuration
                                to the owner(s) of the sendwithus account

#### Sample Request:

```json
{
    "name": "My SendGrid Account",
    "esp_type": "sendgrid",
    "credentials": {
        "username": "mysendgridusername",
        "password": "password123"
    }
}
```


```json
{
    "name": "My Mailgun Account",
    "esp_type": "mailgun",
    "credentials": {
        "api_key": "key-mymailgunapikey",
        "domain": "my.mailgun.domain.com"
    }
}
```


```json
{
    "name": "My Mandrill Account",
    "esp_type": "mandrill",
    "credentials": {
        "api_key": "mymandrillapikey"
    }
}
```


```json
{
    "name": "My Postmark Account",
    "esp_type": "postmark",
    "credentials": {
        "api_key": "my-postmark-api-key"
    }
}
```


```json
{
    "name": "My Message Bus Account",
    "esp_type": "messagebus",
    "credentials": {
        "api_key": "mymessagebusapikey",
        "session_key": "mymessagebussessionkey"
    }
}
```


```json
{
    "name": "My SES Account",
    "esp_type": "ses",
    "credentials": {
        "access_key_id": "mysesaccesskeyid",
        "secret_access_key": "mysessecretaccesskey",
        "region": "us-east-1"
    }
}
```


```json
{
    "name": "My Mailjet Account",
    "esp_type": "mailjet",
    "credentials": {
        "api_key": "mymailjetapikey",
        "secret_key": "mymailjetsecretkey"
    }
}
```


```json
{
    "name": "My Dyn Account",
    "esp_type": "dyn",
    "credentials": {
        "api_key": "mydynapikey"
    }
}
```


```json
{
    "name": "My SMTP Account",
    "esp_type": "smtp",
    "credentials": {
        "host": "smtp.example.com",
        "port": 25,
        "username": "myusername",
        "password": "mypassword",
        "use_tls": true
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

`PUT /esp_accounts/set_default`

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
