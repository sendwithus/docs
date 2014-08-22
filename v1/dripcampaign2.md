# Drip Campaign API 2.0

**Drip Campaigns 2.0 are not live.**  This is simply a sneak preview of what will be available when 2.0 is released, as well as a way for customers to give us feedback on our proposed implementation.

## Activate campaign for a customer
This will add the specified customer to the first step of the specified drip campaign.  If the first step has a delay on it, then it will send the first email once that delay has elapsed.

POST `/drip_campaigns/(campaign_id)/activate`

Params:
- recipient_address -- Email address of the customer you want to add to the specified campaign.

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

## List the customers active on a specific drip campaign
GET `/drip_campaigns/(drip_campaign_id)/customers`

Sample Response

```json
[
    {
        "recipient_address": "customer@example.com",
        "pending_drip_step": {
            "object": "drip_step",
            "id": "dcs_awfmi4MFwm3if$m",
            "email_id": "tem_mMEvmi2MEfjawe",
            "scheduled_time": "2014-08-22 19:48:40.097992+00:00"
        }
    }
]
```