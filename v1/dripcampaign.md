# Drip Campaign API

## Deactivate drip campaigns by email address

POST `/drips/deactivate`
Deactivate all drip campaigns scheduled to send to a specific email address


Sample Request

```json
{
    "email_address": "customer@exmaple.com"
}
```

Sample Response

```json
{
    "success": true,
    "status": "OK",
    "email_address": "customer@example.com",
    "deactivated_count": 1
}
```
