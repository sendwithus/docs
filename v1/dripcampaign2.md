# Drip Campaign API 2.0

## CAMPAIGN API:

## Get a list of campaigns
GET `/drip_campaigns`

Sample Response

```json
[
    {
        "campaign_id": "cmp_m3mfMgMiemni82nm2imGMw",
        "campaign_name": "welcome_campaign",
        "number_of_steps": "14"
    },
    {
        "campaign_id": "cmp_MEitnqi2mGmwiednWN2mwi",
        "campaign_name": "spring_sales_promo",
        "number_of_steps": "3"
    }
]
```

## Create a new campaign
POST `/drip_campaigns`

Sample Request

```json
{
    "campaign_name": "new_campaign",
    "trigger_emails": [
        "tem_EzwLhNe3vdBmwniLwPvfRY",
        "tem_ImjaMEmgiw3mQng9MienwE"
        ],
    "active": "true"
}
```

## Update a campaign
PUT `/drip_campaigns/(campaign_id)`

Sample Request

```json
{
    "campaign_name": "new_campaign",
    "trigger_emails": [
        "tem_EzwLhNe3vdBmwniLwPvfRY",
        "tem_ImjaMEmgiw3mQng9MienwE"
        ],
    "active": "true"
}
```

## Delete a campaign
DELETE `/drip_campaigns/(campaign_id)`

## Deactivate a campaign for customer
POST `/drip_campaigns/(campaign_id)/deactivate`

Sample Request

```json
{
    "email_address": "customer@example.com"
}
```

## Start customer on a campaign
POST `/drip_campaigns/(campaign_id)/activate`

Sample Request

```json
{
    "email_address": "customer@example.com"
}
```

## Get stats on a single campaign
GET `/drip_campaigns/(campaign_id)`

Sample Response

```json
{
    "campaign_name": "welcome_campaign",
    "number_of_steps": "14",
    "pending_customers": "2004",
    "last_30_days": {
        "sent": "4366",
        "unsubscribe_rate": "14.8%",
        "engagement_rate": "35.2%",
    },
    "overall": {
        "sent": "56002",
        "unsubscribe_rate": "7.3%",
        "engagement_rate": "29.4%",
    }
}
```

## STEP API:

## Get a list of steps in a campaign
GET `/drip_campaigns/(campaign_id)/drip_steps`

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

## Create a new step in a campaign
POST `/drip_campaigns/(campaign_id)/drip_steps`

Sample Request

```json
{
    "step_name": "welcome_1",
    "delay_seconds": "600",
    "user_layout": "tem_ImjaMEmgiw3mQng9MienwE",
    "active": "true"
}
```

## Update a step in a campaign
PUT `/drip_campaigns/(campaign_id)/drip_steps/(step_id)`

Sample Request

```json
{
    "step_name": "welcome_1",
    "delay_seconds": "600",
    "user_layout": "tem_ImjaMEmgiw3mQng9MienwE",
    "active": "true"
}
```

## Delete a step
DELETE `/drip_campaign/(campaign_id)/drip_steps/(step_id)

## Deactivate a step for customer
POST `/drip_campaign/(campaign_id)/drip_steps/(step_id)/deactivate`

Sample Request

```json
{
    "email_address": "customer@example.com"
}
```

## Get stats on a single step
GET `/drip_campaigns/(campaign_id)/drip_steps/(step_id)`

Sample Response

```json
{
    "campaign_name": "welcome_campaign",
    "step_name": "followup_2",
    "user_layout": "followup_layout_new",
    "pending_customers": "427",
    "last_30_days": {
        "sent": "836",
        "unsubscribe_rate": "12.8%",
        "engagement_rate": "31.0%",
    },
    "overall": {
        "sent": "7445",
        "unsubscribe_rate": "5.2%",
        "engagement_rate": "28.9%",
    }
}
```