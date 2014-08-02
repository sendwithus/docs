# Internationalization (il8n) API


*NOTE* -- Our internationalization API is under **private beta**. If you'd like access, please reach out to [us@sendwithus.com](mailto:us@sendwithus.com).

### How it works

Sendwithus handles internationalization by using *Jinja2* style trans blocks.

The easiest way to set up templates for translation is to use the trans block syntax. A string can be marked for translation by simply wrapping it in a trans block. For example, the internationalized version of `Hello World` is `{% trans %}Hello World{% endtrans %}`. Variables in trans block can be added like normal template variables. For example `Hello {{ name }}` will become `{% trans %}Hello {{ name }}{% endtrans %}`. Multiple variables can be used in the same trans block.

Translation packages (`.pot` files) can be downloaded via API, and then corresponding string files (`.po`) can be uploaded via API, which will trigger translated template variants to be generated.

## Get translation package (`.pot`)


This call will fetch a `.pot` translation package for all templates that have been assigned the corresponding `tag`

GET `/il8n/pot/(:tag)`

Params:

- tag       -- String will return a `.pot` only for templates that have the corresponding tag. Tags are set in the [dashboard](https://www.sendwithus.com/#/emails)

### Examples

Fetch `.pot` for template with tag `international`

```
curl \
-X GET \
-u swu_api_key: \
https://api.sendwithus.com/api/v1/i18n/pot/international
```

## Post translated strings (`.po`)

Use this endpoint to `POST` a `.zip` file containing `.po` files, each `.po` file named to match the locale it is intended for. See examples below for specifics.

POST `/il8n/po/(:tag)`

Params:

- tag       -- String of tag; templates with that tag applied will have a version generated for each `.po` file in the `.zip` file

Request Body:

- `.zip` file


### Examples

Example `.zip` structure:

```
translations.zip
    en-US.po
    ja-JP.po
```

Post `translations.zip` for templates with tag `international`

```
curl \
-X POST \
-u swu_api_key: \
--data-binary @translations.zip \
https://api.sendwithus.com/api/v1/i18n/po/international
```

## Sending translated templates

At send time, Sendwithus uses the `version_name` parameter in the `send` API, and matches it against the template version for that locale. This is why `.po` files must have a filename that matches the locale.

For an example sending with a translated template, please see the [send api](../master/v1/send.md) documentation.
