# Drip Campaign API 2.0

CAMPAIGN API:

## Get a list of campaigns
GET `/drip_campaigns`

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


STEP API:

## Get a list of steps in a campaign
GET `/drip_campaigns/(campaign_id)/drip_steps`

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