---
title: Templates
type: api
order: 0
---

# Templates API

If no locale is specified in the URL the default locale will be used in all cases.

*NOTE* -- All parameters are mandatory unless otherwise noted.

## Get a List of Templates

`GET /templates`

#### Sample Response:

```json
[
    {
        "id": "Template ID",
        "name": "Template Name",
        "locale": "en-US",
        "created": "created unix timestamp",
        "versions": [
            {
                "name": "Version Name",
                "id": "Version ID",
                "published": true,
                "created": "created unix timestamp",
                "modified": "modified unix timestamp"
            }
        ],
        "tags": ["tag1", "tag2"]
    }
]
```

## Get a specific template (all versions)

`GET /templates/(:template_id)`

`GET /templates/(:template_id)/locales/(:locale)`

#### Sample Response:

```json
{
    "id": "tem_hQf1VnmCNrPjBdYQPOpLZ9",
    "name": "Template Name",
    "created": 1411606421,
    "locale": "en-US",
    "versions": [
        {
            "name": "Version Name",
            "id": "ver_rmU8gMtRTYpwQcpYaPnB5p",
            "published": true,
            "created": "created unix timestamp",
            "modified": "modified unix timestamp"
        }
    ],
    "tags": ["tag1", "tag2"]
}
```

## Get a list of template versions (with HTML/text)

`GET /templates/(:template_id)/versions`

`GET /templates/(:template_id)/locales/(:locale)/versions`

#### Sample Response:

```json
[
    {
        "id": "tem_hQf1VnmCNrPjBdYQPOpLZ9",
        "created": 1411606421,
        "modified": 1411610000,
        "published": true,
        "name": "Version 1",
        "html": "<html>...</html>",
        "text": "Hello World",
        "subject": "My Subject"
    },
    {
        "id": "tem_hQf1VnmCNrPjBdYQPOpLZ8",
        "created": 1411606706,
        "modified": 1411610000,
        "published": false,
        "name": "Version 2",
        "html": "<html>...</html>",
        "text": "Hello World Again",
        "subject": "My Subject Again"
    }
]
```

## Get a specific version (with HTML/text)

`GET /templates/(:template_id)/versions/(:version_id)`

`GET /templates/(:template_id)/locales/(:locale)/versions/(:version_id)`

#### Sample Response:

```json
{
    "id": "tem_hQf1VnmCNrPjBdYQPOpLZ9",
    "created": 1411606706,
    "modified": 1411610000,
    "published": true,
    "name": "Version Name",
    "html": "<html>...</html>",
    "text": "Hello World",
    "subject": "My Subject"
}
```

## Update a Template Version

`PUT /templates/(:template_id)/versions/(:version_id)`

`PUT /templates/(:template_id)/locales/(:locale)/versions/(:version_id)`

#### Params:

- name       -- The version name of the template
- subject    -- The subject line of the template
- preheader (optional) -- The preheader of the template
- html (optional) -- The HTML body of the template
- text (optional) -- The Plain Text body of the template
- amp_html (optional) -- The AMPHTML body of the template
- template_data (optional) -- The Sample Data of the template

*NOTE* -- At least one of html or text must be specified

*NOTE* -- This will replace the current version of the specified template

#### Sample Request:

```json
{
    "html": "<html><head></head><body><h1>UPDATED TEMPLATE VERSION</h1></body></html>",
	"name": "New Version",
	"subject": "Edited Subject!",
	"preheader": "Edited Preheader",
	"template_data": {
		"example": "name1_updated",
		"example2": [
			"one_updated",
			"two_updated"
		]
	},
	"text": "Updated text",
	"amp_html": "<html amp4email><head></head><body>UPDATED TEMPLATE VERSION AMPHTML</body></html>"
}
```

#### Sample Response:

```json
{
    "id": "ver_RjEBErY6eXBPpgYt269iJU",
    "created": 1408394344,
    "modified": 1408424322,
    "published": true,
    "name": "New Version",
    "html": "<html><head></head><body><h1>UPDATED TEMPLATE VERSION</h1></body></html>",
	"text": "Updated text",
	"subject": "Edited Subject!",
	"preheader": "Edited Preheader",
	"template_data": {
		"example": "name1_updated",
		"example2": [
			"one_updated",
			"two_updated"
		]
	},
	"amp_html": "<html amp4email><head></head><body>UPDATED TEMPLATE VERSION AMPHTML</body></html>"
}
```

## Create a New Template

`POST /templates`

#### Params:

- name       -- The name of the template
- subject    -- The subject line of the template
- preheader (optional) -- The preheader of the template
- html (optional) -- The HTML body of the template
- text (optional) -- The Plain Text body of the template
- amp_html (optional) -- The AMPHTML body of the template
- template_data (optional) -- The Sample Data of the template
- locale (optional) -- The locale code of the template (defaults to en-US)

*NOTE* -- At least one of html or text must be specified

#### Sample Request:

```json
{
	"html": "<html><head></head><body><h1>NEW TEMPLATE</h1></body></html>",
	"name": "New Template",
	"subject": "This is a new template!",
	"preheader": "This is a preheader",
	"template_data": {
		"example": "name1",
		"example2": [
			"one",
			"two"
		]
	},
	"text": "some text",
	"locale": "en-US",
	"amp_html": "<html amp4email><head></head><body>NEW TEMPLATE AMPHTML</body></html>"
}
```

#### Sample Response:

```json
{
    "id": "tem_ACdWZKZf4CtZNPM27WAdf6",
    "locale": "en-US",
    "name": "New Template"
}
```

## Add Locale to Existing Template

`POST /templates/(:template_id)/locales`

### Params:

- name       -- The name of the initial version
- subject    -- The subject line of the template
- locale     -- The locale code of the new template
- html (optional) -- The HTML body of the template
- text (optional) -- The Plain Text body of the template

*NOTE* -- At least one of html or text must be specified

#### Sample Request:

```json
{
    "html": "<html><head></head><body><h1>Nouveau modèle!</h1></body></html>",
    "name": "Published French Version",
    "subject": "Ce est un nouveau modèle!",
    "locale": "fr-FR",
    "text": "un texte"
}
```

#### Sample Response:

```json
{
    "id": "tem_ACdWZKZf4CtZNPM27WAdf6",
    "locale": "fr-FR",
    "name": "A New Template",
    "version_id": "ver_RjEBErY6eXBPpgYt269iJU"
}
```

## Create a New Template Version

`POST /templates/(:template_id)/versions`

`POST /templates/(:template_id)/locales/(:locale)/versions`

#### Params:

- name       -- The version name of the template
- subject    -- The subject line of the template
- preheader (optional) -- The preheader of the template
- html (optional) -- The HTML body of the template
- text (optional) -- The Plain Text body of the template
- amp_html (optional) -- The AMPHTML body of the template
- template_data (optional) -- The Sample Data of the template

*NOTE* -- At least one of html or text must be specified

#### Sample Request:

```json
{
	"html": "<html><head></head><body><h1>NEW TEMPLATE VERSION</h1></body></html>",
	"name": "New Template",
	"subject": "New Version!",
	"preheader": "This is a preheader",
	"template_data": {
		"example": "name1",
		"example2": [
			"one",
			"two"
		]
	},
	"text": "some text",
	"locale": "en-US",
	"amp_html": "<html amp4email><head></head><body>NEW TEMPLATE VERSION AMPHTML</body></html>"
}
```

#### Sample Response:

```json
{
    "id": "ver_s6a68dJuz6Rn8dypq4j4Qo",
    "created": 1410808743,
    "modified": 1410808900,
    "published": false,
    "name": "New Template Version",
    "html": "<html><head></head><body><h1>NEW TEMPLATE VERSION</h1></body></html>",
    "text": "some text",
    "subject": "New Version!",
    "preheader": "This is a preheader",
	"template_data": {
		"example": "name1",
		"example2": [
			"one",
			"two"
		]
	},
	"amp_html": "<html amp4email><head></head><body>NEW TEMPLATE VERSION AMPHTML</body></html>"
}
```

## Delete a specific template

`DELETE /templates/(:template_id)`

`DELETE /templates/(:template_id)/locales/(:locale)`

*NOTE* -- all versions and locales will be deleted unless a locale is specified

#### Sample Response:

```json
{
    "success": true,
    "status": "OK"
}
```
