# Render API

The `render` api allows you to render a template with data, using the exact same rendering workflow that Sendwithus uses when delivering your email.

*NOTE* -- All parameters are mandatory unless otherwise noted.

## Render a Template with Data


POST `/send`

Params:

- email_id       -- Unique ID obtained from /emails
- recipient
   - address -- The recipient's email address
   - name (optional) -- The recipient's name
- cc (optional)     -- An array of CC recipients, each of the format
    - address -- CC Address
    - name -- CC Name
- bcc (optional)        -- An array of CC recipients, each of the format
    - address -- CC Address
    - name -- CC Name
- sender (optional)
   - address    -- The sender's email address
   - reply_to   -- The sender's reply-to address
   - name       -- The sender's name
- email_data    -- Object containing email template data
- version_name (optional) -- Name of the template version to send (overrides A/B tests and test api keys)

Sample Request:

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

  "version_name": "Optional, name of template version"
}
```

Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "template": {
        "id": "Template ID",
        "name": "Template name",
        "version_name": "Template version name"
    },
    "subject": "RENDERED SUBJECT WITH DATA",
    "html": "RENDERED HTML BODY WITH DATA",
    "text": "RENDERED TEXT BODY WITH DATA"
}
```