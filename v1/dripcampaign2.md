# Drip Campaign API 2.0

**Drip Campaigns 2.0 are not live.**  This is simply a sneak preview of what will be available when 2.0 is released, as well as a way for customers to give us feedback on our proposed implementation.

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

## Deactivate a campaign for customer
POST `/drip_campaigns/(campaign_id)/deactivate`

Sample Request

```json
{
    "email_address": "customer@example.com"
}
```

Sample Response

```json
{
    "success": true,
    "campaign_id": "cmp_MEitnqi2mGmwiednWN2mwi",
    "email_address": "customer@example.com"
}
```

## Start customer on a campaign
This will add the specified customer to the first step of the specified drip campaign.  If the first step has a delay on it, then it will send the first email once that delay has elapsed.  This is the alternative way to start a campaign (as opposed to using trigger emails).

POST `/drip_campaigns/(campaign_id)/start`

Sample Request

```json
{
    "email_address": "customer@example.com"
}
```

Sample Response

```json
{
    "success": true,
    "campaign_id": "cmp_MEitnqi2mGmwiednWN2mwi",
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
        "bounced": "241",
        "unsubscribe_rate": "14.8%",
        "open_rate": "31.0%",
        "click_rate": "11.7%",
    },
    "overall": {
        "sent": "56002",
        "bounced": "241",
        "unsubscribe_rate": "7.3%",
        "open_rate": "21.4%",
        "click_rate": "8.5%",
    }
}
```

## CAMPAIGN STEP API:

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

## Deactivate a step for customer
POST `/drip_campaign/(campaign_id)/drip_steps/(step_id)/deactivate/`

Sample Request

```json
{
    "email_address": "customer@example.com"
}
```

Sample Response

```json
{
    "success": true,
    "campaign_id": "cmp_MEitnqi2mGmwiednWN2mwi",
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
        "bounced": "241",
        "unsubscribe_rate": "12.8%",
        "open_rate": "31.0%",
        "click_rate": "11.7%",
    },
    "overall": {
        "sent": "7445",
        "bounced": "241",
        "unsubscribe_rate": "5.2%",
        "open_rate": "21.4%",
        "click_rate": "8.5%",
    }
}
```