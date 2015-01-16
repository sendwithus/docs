# Send API

*NOTE* -- All parameters are mandatory unless otherwise noted.

## Send an Email

POST `/send`

#### Params:

- email_id                  -- Template ID to send
- recipient
   - address                -- The recipient's email address
   - name (optional)        -- The recipient's name
- cc                        -- An array of CC recipients, of the format {"address":"cc@email.com"}
- bcc                       -- An array of BCC recipients, of the format {"address":"bcc@email.com"}
- sender (optional)
   - address                -- The sender's email address
   - reply_to               -- The sender's reply-to address
   - name                   -- The sender's name
- email_data                -- Object containing email template data
- tags (optional)           -- Array of tags (as strings)
- headers (options)         -- Object contain SMTP headers to be included with the email
- inline (optional)         -- Inline attachment object (see example)
- files (optional)          -- List of file attachments (combined maximum 7MB, see example)
- esp\_account (optional)   -- ID of the ESP Account to send this email through. ex: esp\_1a2b3c4d5e
- locale (optional)         -- Template locale to send (ie: en-US)
- version_name (optional)   -- Name of the template version to send (overrides A/B tests and test api keys)

#### Sample Request:

```json
{
  "email_id": "tem_A5RHVP6CnRbS34UysLjYHx",
  "recipient": {
    "name": "John",
    "address": "user@email.com"
  },
  "email_data": { "amount": "$12.00" },

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
    "X-HEADER-ONE": "header-value",
    "Return-Path": "sender@yourcompany.com"
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

  "esp_account": "esp_1a2b3c4d5e"
}
```

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "receipt_id": unqiue_receipt_id,
    "email": {
        "name": "NAME OF EMAIL",
        "version_name": "NAME OF VERSION",
        "locale": "en-US"
    }
}
```

#### Sample il8n Request:

```json
{
  "email_id": "tem_A5RHVP6CnRbS34UysLjYHx",

  "recipient": {
    "name": "John",
    "address": "user@email.com"
  },

  "email_data": { "amount": "$12.00" },

  "locale": "en-US"
}
```
