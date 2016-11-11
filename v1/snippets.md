---
title: Snippets
type: api
order: 3
---

# Snippets API

*NOTE* -- All parameters are mandatory unless otherwise noted.

## Get all snippets

`GET /snippets`

#### Sample Response:

```json
[
    {
        "object": "snippet",
        "id": "snp_Q33jTLFc2ayG9KrF2Vcm4F",
        "name": "My First Snippet",
        "body": "<h1>Welcome!</h1>",
        "created": 5858858124,
        "modified": 5938868250
    }
]
```

## Get specific snippet

`GET /snippets/(:id)`

#### Sample Response:

```json
{
    "object": "snippet",
    "id": "snp_Q33jTLFc2ayG9KrF2Vcm4F",
    "name": "My First Snippet",
    "body": "<h1>Welcome!</h1>",
    "created": 5858858124,
    "modified": 5938868250
}
```

## Creating a new snippet

`POST /snippets`

#### Params:

- name       -- Name of the snippet
- body       -- Contents for the snippet

#### Sample Request:

```json
{
    "name": "My First Snippet",
    "body": "<h1>Welcome!</h1>"
}
```

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "snippet": {
        "object": "snippet",
        "id": "snp_Q33jTLFc2ayG9KrF2Vcm4F",
        "name": "My First Snippet",
        "body": "<h1>Welcome!</h1>",
        "created": 5858858124,
        "modified": 5938868250
    }
}
```

## Update an existing snippet

`PUT /snippets/(:id)`

#### Params:

- name       -- Name of the snippet
- body       -- Contents for the snippet

#### Sample Request:

```json
{
    "name": "My First Snippet",
    "body": "<h1>Welcome!</h1>"
}
```

#### Sample Response:

```json
{
    "success": true,
    "status": "OK",
    "snippet": {
        "object": "snippet",
        "id": "snp_Q33jTLFc2ayG9KrF2Vcm4F",
        "name": "My First Snippet",
        "body": "<h1>Welcome!</h1>",
        "created": 5858858124,
        "modified": 5938868250
    }
}
```

## Delete an existing snippet

`DELETE /snippets/(:id)`

#### Sample Response:

```json
{
    "success": true,
    "status": "OK"
}
```
