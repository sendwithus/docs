# Drip Campaign API 2.0

## Activate campaign for a customer
This will add the specified customer to the first step of the specified drip campaign.  If the first step has a delay on it, then it will send the first email once that delay has elapsed.

POST `/drip_campaigns/(drip_campaign_id)/activate`

Params:
- recipient
   - address -- The recipient's email address
   - name (optional) -- The recipient's name
- cc (optional)  -- An array of CC recipients, of the format {"address":"cc@email.com"}
- bcc (optional) -- An array of BCC recipients, of the format {"address":"bcc@email.com"}
- sender (optional)
   - address    -- The sender's email address
   - reply_to   -- The sender's reply-to address
   - name       -- The sender's name
- email_data (optional) -- Object containing email template data
- tags (optional)           -- Array of tags (as strings)
- esp\_account (optional)    -- ID of the ESP Account to send this email through. ex: esp\_1a2b3c4d5e

Sample Request

```json
{
    "recipient": {
    "address": "customer@example.com"
    }
}
```

Sample Request with data

```json
{
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

  "esp_account": "esp_1a2b3c4d5e"
}
```

Sample Response

```json
{
    "success": true,
    "status": "OK",
    "drip_campaign": {
        "id": "dc_m3mfMgMiemni82nm2imGMw",
        "name": "welcome_campaign"
    },
    "recipient_address": "customer@example.com",
    "message": "Recipient successfully added to drip campaign."
}
```

## Deactivate a campaign for customer
POST `/drip_campaigns/(drip_campaign_id)/deactivate`

Params:
- recipient_address -- Email address of the customer you would like to remove from the specified campaign.

Sample Request

```json
{
    "recipient_address": "customer@example.com"
}
```

Sample Response

```json
{
    "success": true,
    "status": "OK",
    "drip_campaign": {
        "id": "dc_m3mfMgMiemni82nm2imGMw",
        "name": "welcome_campaign"
    },
    "recipient_address": "customer@example.com",
    "message": "Recipient successfully removed from drip campaign."
}
```

## Deactivate a customer from all campaigns
POST `/drip_campaigns/deactivate`

Params:
- recipient_address -- Email address of the customer you would like to remove from all drip campaigns.

Sample Request

```json
{
    "recipient_address": "customer@example.com"
}
```

Sample Response

```json
{
    "success": true,
    "status": "OK",
    "recipient_address": "customer@example.com",
    "unsubscribed_count": 14
}
```

## Get a list of campaigns
GET `/drip_campaigns`

Sample Response

```json
[
    {
        "object": "drip_campaign",
        "id": "dc_m3mfMgMiemni82nm2imGMw",
        "name": "welcome_campaign",
        "enabled": true,
        "trigger_email_id": null,
        "drip_steps": [
            {
                "object": "drip_step",
                "id": "dcs_MEitnqi2mGmwiednWN2mwi",
                "email_id": "tem_asdfjkl1234qwer",
                "delay_seconds": "600"
            },
            {
                "object": "drip_step",
                "id": "dcs_MEitn234mGmwiednWN2mwi",
                "email_id": "tem_asdwtgs1234qwer",
                "delay_seconds": "3600"
            }
        ]
    },
    {
        "object": "drip_campaign",
        "id": "dc_m3mfMgafasdi8gadbwEgv",
        "name": "sales_campaign",
        "enabled": true,
        "trigger_email_id": "tem_wneiam3igmiocbmw",
        "drip_steps": [
            {
                "object": "drip_step",
                "id": "dcs_MEitnf2egbDwiednWN2mwi",
                "email_id": "tem_asdwGFWrb234qwer",
                "delay_seconds": "7200"
            }
        ]
    }
]
```

## Get the details on a specific drip campaign
GET `/drip_campaigns/(drip_campaign_id)`

Sample Response

```json
{
    "object": "drip_campaign",
    "id": "dc_m3mfMgMiemni82nm2imGMw",
    "name": "welcome_campaign",
    "enabled": true,
    "trigger_email_id": null,
    "drip_steps": [
        {
            "object": "drip_step",
            "id": "dcs_MEitnqi2mGmwiednWN2mwi",
            "email_id": "tem_asdfjkl1234qwer",
            "delay_seconds": "600"
        },
        {
            "object": "drip_step",
            "id": "dcs_MEitn234mGmwiednWN2mwi",
            "email_id": "tem_asdwtgs1234qwer",
            "delay_seconds": "3600"
        }
    ]
}
```

## Get a list of customers pending on a specific drip campaign
Get `/drip_campaigns/(drip_campaign_id)/customers`

Sample Response

```json
{
    "object": "drip_campaign",
    "id": "dc_m3mfMgMiemni82nm2imGMw",
    "pending_recipients": [
        {
            "recipient_address": "customer@example.com",
            "drip_step_id": "dcs_MEitnqi2mGmwiednWN2mwi"
        },
        {
            "recipient_address": "jimbo@jones.com",
            "drip_step_id": "dcs_MEitn234mGmwiednWN2mwi"
        }
    ]
}
```

## Get a list of customers pending on a specific drip campaign step
Get `/drip_campaigns/(drip_campaign_id)/steps/(drip_step_id)/customers`

Sample Response

```json
{
    "object": "drip_step",
    "id": "dcs_MEitnqi2mGmwiednWN2mwi",
    "pending_recipients": [
        {
            "recipient_address": "jimbo@jones.com",
            "scheduled_send_time": "2014-08-27 20:25:44.301744+00:00"
        },
        {
            "recipient_address": "tinaturner@sendwithus.com",
            "scheduled_send_time": "2014-08-29 16:32:44.301744+00:00"
        }
    ]
}
```