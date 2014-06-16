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

## Get a specific template (all versions)

GET `/templates/(:template_id)`

Sample Response:
```json
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
	}
```

## Get a specific version (with HTML/text)

GET `/templates/(:template_id)/(:version_id)`

Sample Response:
```json
    {
    	"id": "Template ID",
        "published": True,
        "created": "created unix timestamp",
        "name": "Name of version",
        "html": "(raw template html)",
        "text": "(raw template text)",
        "subject": "(version subject)"
	}
```

## Updating a Template Version

PUT `/templates/(:template_id)/versions/(:version_id)`

Params:
- html       -- The HTML body of the template
- name       -- The name of the template
- subject    -- The subject line of the template
- text (opt) -- The Text body of the template

*NOTE* -- One of html or text must be specified
*NOTE* -- This will replace the current template version

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
