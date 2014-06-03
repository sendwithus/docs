# Templates API


*NOTE* -- All parameters are mandatory unless otherwise noted.

## Get a List of Templates

GET `/templates`

Returns a JSON list of all templates in your account

Sample Response:
```json
[
    {
    	"id": "Template ID",
        "name": "Template Name",
        "created": "created unix timestamp",
        "versions": [
        	{
            	"name": "Version Name",
                "id": "Version ID"
            }
        ],
        "tags": ["tag1", "tag2"]
	}, ...
]
```

## Creating a New Template


POST `/templates`

Params:
- html       -- The HTML body of the template
- name       -- The name of the template
- subject    -- The subject line of the template
- text (opt) -- The Text body of the template

## Creating a New Template Version 

POST `/templates/(:template_id)/versions`

Params:
- html       -- The HTML body of the template
- name       -- The name of the template
- subject    -- The subject line of the template
- text (opt) -- The Text body of the template

*NOTE* -- One of html or text must be specified

## Updating a Template Version

PUT `/templates/(:template_id)/versions/(:version_id)`

Params:
- html       -- The HTML body of the template
- name       -- The name of the template
- subject    -- The subject line of the template
- text (opt) -- The Text body of the template

*NOTE* -- One of html or text must be specified
*NOTE* -- This will replace the current template version
