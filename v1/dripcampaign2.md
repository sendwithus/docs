# Drip Campaign API 2.0

CAMPAIGN API:

## Get a list of campaigns
GET /drip_campaigns

## Create a new campaign
POST /drip_campaigns
    "campaign_name"
    "trigger_emails"
    "active"

## Update a campaign
PUT /drip_campaigns/(campaign_id)
    "campaign_name"
    "trigger_emails"
    "active"

## Delete a campaign
DELETE /drip_campaigns/(campaign_id)

## Deactivate a campaign for customer
POST /drip_campaigns/(campaign_id)/deactivate
    "email_address"

## Start customer on a campaign
POST /drip_campaigns/(campaign_id)/activate
    "email_address"

## Get stats on a single campaign
GET /drip_campaigns/(campaign_id)


STEP API:

## Get a list of steps in a campaign
GET /drip_campaigns/(campaign_id)/drip_steps

## Create a new step in a campaign
POST /drip_campaigns/(campaign_id)/drip_steps
    "step_name"
    "delay_seconds" rework?
    "user_layout"

## Update a step in a campaign
PUT /drip_campaigns/(campaign_id)/drip_steps/(step_id)
    "step_name"
    "delay_seconds" rework?
    "user_layout"

## Delete a step
DELETE /drip_campaign/(campaign_id)/drip_steps/(step_id)

## Deactivate a step for customer
POST /drip_campaign/(campaign_id)/drip_steps/(step_id)/deactivate
    "email_address"

## Get stats on a single step
GET /drip_campaigns/(campaign_id)/drip_steps/(step_id)