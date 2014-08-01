# Drip Campaign API 2.0

**Drip Campaigns 2.0 are not live.**  This is simply a sneak preview of what will be available when 2.0 is released, as well as a way for customers to give us feedback on our proposed implementation.

## DRIP CAMPAIGN API:

## Start customer on a campaign
This will add the specified customer to the first step of the specified drip campaign.  If the first step has a delay on it, then it will send the first email once that delay has elapsed.

POST `/drip_campaigns/(campaign_id)/activate`

Params:
    recipient_address --
    start_step (optional) --

Sample Request

```json
{
    "recipient_address": "customer@example.com",
    "start_step": "drp_MEitnqi2mGmwiednWN2mwi"
}
```

Sample Response

```json
{
    "activated": "true",
    "campaign_id": "drp_MEitnqi2mGmwiednWN2mwi",
    "email_address": "customer@example.com"
}
```

## Get a list of campaigns
GET `/drip_campaigns`

Sample Response

```json
[
    {
        "campaign_id": "drp_m3mfMgMiemni82nm2imGMw",
        "campaign_name": "welcome_campaign",
        "trigger_layout": "tem_ImjaMEmgiw3mQng9MienwE",
        "steps": [
            {
                "step_id": "stp_MEitnqi2mGmwiednWN2mwi",
                "step_name": "some_step"
            },
            {
                "step_id": "stp_Mawiefmfiwme2AN2mwi",
                "step_name": "another_step"
            }
        ]
    },
    {
        "campaign_id": "drp_MEitnqi2mGmwiednWN2mwi",
        "campaign_name": "spring_sales_promo",
        "trigger_layout": "None",
        "steps": [
            {
                "step_id": "stp_MEitnqi2mFFFiednWN2mwi",
                "step_name": "crazy_step"
            }
        ]
    }
]
```

## Deactivate a campaign for customer
POST `/drip_campaigns/(campaign_id)/deactivate`

Params:
    recipient_address --

Sample Request

```json
{
    "recipient_address": "customer@example.com"
}
```

Sample Response

```json
{
    "deactivated": "false",
    "message": "Customer not active on specified campaign."
    "campaign_id": "cmp_MEitnqi2mGmwiednWN2mwi",
    "recipient_address": "customer@example.com"
}
```

## DRIP STEP API:

## Get a list of steps in a campaign
GET `/drip_campaigns/(campaign_id)/drip_steps`

Sample Response

```json
[
    {
        "step_id": "stp_m3mfMgMiemni82nm2imGMw",
        "step_name": "step_1",
        "user_layout": "tem_ImjaMEmgiw3mQng9MienwE",
        "delay_seconds": "600"
    },
    {
        "step_id": "cmp_MEitnqi2mGmwiednWN2mwi",
        "step_name": "step_2",
        "user_layout": "tem_m4fmweimWM29MpoiemE8Nn",
        "delay_seconds": "3600"
    }
]
```
