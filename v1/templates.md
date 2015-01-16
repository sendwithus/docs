# Templates API

*NOTES:*
- All parameters are mandatory unless otherwise noted.
- If no locale is specified in the URL, the default local will be used in all cases.

## Get a List of Templates

GET `/templates`

Get a list of all templates

#### Sample Response:

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
    }
]
```

## Get a specific template (all versions)

GET `/templates/(:template_id)`

#### Sample Response:

```json
{
    "id": "tem_jluyjluyjlyu",
    "name": "Template Name",
    "created": 1411606421,
    "versions": [
        {
            "name": "Version Name",
            "id": "ver_arstneiotsra"
        }
    ],
    "tags": ["tag1", "tag2"]
}
```

## Get a list of template versions (with HTML/text)

GET `/templates/(:template_id)[/locales/(:locale)]/versions`

#### Sample Response:

```json
[
    {
        "id": "tem_arstarstarst",
        "published": true,
        "created": 1411606421,
        "name": "Version 1",
        "html": "<html>...</html>",
        "text": "Hello World",
        "subject": "My Subject"
    },
    {
        "id": "tem_qwfpqwfpqwfp",
        "published": false,
        "created": 1411606706,
        "name": "Version 2",
        "html": "<html>...</html>",
        "text": "Hello World Again",
        "subject": "My Subject Again"
    }
]
```

## Get a specific version (with HTML/text)

GET `/templates/(:template_id)[/locales/(:locale)]/versions/(:version_id)`

#### Sample Response:

```json
{
    "id": "ver_arstarstarst",
    "published": true,
    "created": 1411606706,
    "name": "Version Name",
    "html": "<html>...</html>",
    "text": "Hello World",
    "subject": "My Subject"
}
```

## Update a Template Version

PUT `/templates/(:template_id)[/locales/(:locale)]/versions/(:version_id)`

#### Params:

- name       -- The name of the template
- subject    -- The subject line of the template
- html (optional) -- The HTML body of the template
- text (optional) -- The Text body of the template

*NOTE* -- At least one of html or text must be specified

*NOTE* -- This will replace the current version of the specified template

#### Sample Request:

```
{
    "html": "<html><head></head><body><h1>UPDATE</h1></body></html>",
    "name": "New Version",
    "subject": "edited!",
    "text": "sometext"
}
```

#### Sample Response:

```json
{
    "created": 1408394344,
    "html": "<html><head></head><body><h1>UPDATE</h1></body></html>",
    "id": "ver_RjEBErY6eXBPpgYt269iJU",
    "name": "New Version",
    "published": true,
    "subject": "edited!",
    "text": "sometext"
}
```
## Create a New Template

POST `/templates`

#### Params:

- name       -- The name of the template
- subject    -- The subject line of the template
- html (optional) -- The HTML body of the template
- text (optional) -- The Text body of the template

*NOTE* -- At least one of html or text must be specified

#### Sample Request:

```json
{
    "html": "<html><head></head><body><h1>NEW TEMPLATE</h1></body></html>",
    "name": "New Template",
    "subject": "This is a new template!",
    "text": "some text"
}
```

#### Sample Response:

```json
{
    "id": "tem_ACdWZKZf4CtZNPM27WAdf6",
    "name": "A New Template"
}
```

## Create a New Template Version

POST `/templates/(:template_id)[/locales/(:locale)]/versions`

#### Params:

- name       -- The name of the template
- subject    -- The subject line of the template
- html (optional) -- The HTML body of the template
- text (optional) -- The Text body of the template

*NOTE* -- At least one of html or text must be specified

#### Sample Request:

```json
{
    "html": "<html><head></head><body><h1>NEW TEMPLATE VERSION</h1></body></html>",
    "name": "New Template Version",
    "subject": "New Version!",
    "text": "some text"
}
```

#### Sample Response:

```json
{
    "created": 1410808743,
    "html": "<html><head></head><body><h1>NEW TEMPLATE VERSION</h1></body></html>",
    "id": "ver_s6a68dJuz6Rn8dypq4j4Qo",
    "name": "New Template Version",
    "published": false,
    "subject": "New Version!",
    "text": "some text"
}
```
