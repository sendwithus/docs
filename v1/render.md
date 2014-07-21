# Render API

The `render` api allows you to render a template with data, using the exact same rendering workflow that Sendwithus uses when delivering your email.

*NOTE* -- All parameters are mandatory unless otherwise noted.

## Render a Template with Data


POST `/render`

Params:

- template_id     -- Unique ID obtained from /emails
- template_data   -- Object containing email template data

Sample Request:

```json
{
  "template_id": "tem_A5RHVP6CnRbS34UysLjYHx",
  "template_data": { "amount": "$12.00" }
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
