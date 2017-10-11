---
title: Sending Emails
type: api
order: 1
---

# Send API

*NOTE* -- All parameters are mandatory unless otherwise noted.

*NOTE* -- If a customer does not exist by the specified email, this call will create a customer.

## Send an Email

`POST /send`

#### Params:

- template                  -- Template ID to send
- recipient
   - address                -- The recipient's email address
   - name (optional)        -- The recipient's name
- cc (optional)             -- An array of CC recipients, of the format {"address":"cc@email.com"}
- bcc (optional)            -- An array of BCC recipients, of the format {"address":"bcc@email.com"}
- sender (optional)
   - address                -- The sender's email address
   - reply_to               -- The sender's reply-to address
   - name                   -- The sender's name
- template_data (optional)  -- Object containing email template data (maximum 128KB)
- tags (optional)           -- Array of tags (as strings). _Tags are passed to your ESP as Categories, Tags, etc._
- headers (optional)         -- Object contain SMTP headers to be included with the email
- inline (optional)         -- Inline attachment object (see example)
- files (optional)          -- List of file attachments (combined maximum 7MB, see example)
- esp\_account (optional)   -- ID of the ESP Account to send this email through. ex: esp\_1a2b3c4d5e
- locale (optional)         -- Template locale to send (ie: en-US)
- version_name (optional)   -- Name of the template version to send (overrides A/B tests)

#### Sample Request:

```json
{
    "template": "tem_A5RHVP6CnRbS34UysLjYHx",
    "recipient": {
        "name": "John",
        "address": "user@email.com"
    },
    "template_data": { "amount": "$12.00" },
    "cc": [
        {"address": "cc_one@email.com"},
        {"address": "cc_two@email.com"}
    ],
    "bcc": [
        {"address": "bcc_one@email.com"},
        {"address": "bcc_two@email.com"}
    ],
    "sender": {
        "name": "Company",
        "address": "company@company.com",
        "reply_to": "info@company.com"
    },
    "tags": [
        "tag1",
        "tag2",
        "tag3"
    ],
    "headers": {
        "X-HEADER-ONE": "header-value"
    },
    "inline": {
        "id": "cat.png",
        "data": "{BASE_64_ENCODED_FILE_DATA}"
    },
    "files": [
        {
            "id": "doc.txt",
            "data": "{BASE_64_ENCODED_FILE_DATA}"
        },
        {
            "id": "stuff.zip",
            "data": "{BASE_64_ENCODED_FILE_DATA}"
        }
    ],
    "locale": "en-US",
    "esp_account": "esp_1a2b3c4d5e",
    "version_name": "Version Name"
}
```

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "receipt_id": "log_asdf1234qwerty",
    "email": {
        "name": "NAME OF EMAIL",
        "version_name": "NAME OF VERSION",
        "locale": "en-US"
    }
}
```

## Inline Images

#### Sample Request Code

```json
{
    "template": "tem_9UPo9P7qMr8qHwHvPhDjP6F6f",
    "recipient": {
        "name": "John",
        "address": "customer@example.com"
    },
    "inline": {
        "id": "happy.png",
        "data": "iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAMAAAC6V+0/AAAANlBMVEX1zHX///////70znj31I799eP20YP53qb879P879V/XjXTrWO5lFSgfUbYsWWOazx0Ui+DYjfNsfnyAAAAfUlEQVQYlXWQ2w6AIAxDK3KTIej//6yboiiZfWjGSZaVYlKE000MHvAhmg6dRZN1N1xmPJqXC7oXY+oEGouPrGEYZaq1e2QYZEipe2DoMcgzHBnwB2W90PWk0tblEG1ZWN6oHTojlT2ta9rLHamFp5yph1e/qReiV6eXPOoAcMkDL0/NWToAAAAASUVORK5CYII="
    }
}
```

#### Sample Template Code

```html
<img src="cid:happy.png" alt="a happy face">
```
