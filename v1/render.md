---
title: Rendering Templates
type: api
order: 4
---
# Render API

The render api allows you to render a template with data, using the exact same rendering workflow that Sendwithus uses when delivering your email.

*NOTE* -- All parameters are mandatory unless otherwise noted.

## Render a Template with Data


`POST /render`

#### Params:

- template_id               -- Template ID
- template_data             -- Object containing email template data
- version\_id (optional)    -- Version ID obtained from /templates/(:template_id)/versions
- version\_name (optional)  -- Version name that you want rendered (provide either a version_name or a version_id, not both)
- locale (optional)         -- Template locale to render

#### Sample Request:

```json
{
  "template_id": "tem_A5RHVP6CnRbS34UysLjYHx",
  "template_data": { "amount": "$12.00" },
  "version_id": "ver_r4nd0ml3tt3rsv15h4l0l",
  "locale": "en-US"
}
```

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "template": {
        "id": "ver_r4nd0ml3tt3rsv15h4l0l",
        "name": "Template name",
        "version_name": "Template version name",
        "locale": "en-US"
    },
    "subject": "RENDERED SUBJECT WITH DATA",
    "html": "RENDERED HTML BODY WITH DATA",
    "text": "RENDERED TEXT BODY WITH DATA"
}
```
