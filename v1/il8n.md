---
title: Multi-Language
type: api
order: 11
---

# Internationalization (il8n) API


*NOTE* -- Our internationalization API is under **private beta**. If you'd like access, please reach out to [us@sendwithus.com](mailto:us@sendwithus.com).

### How it works

Sendwithus handles internationalization by using *Jinja2* style trans blocks.

The easiest way to set up templates for translation is to use the trans block syntax. A string can be marked for translation by simply wrapping it in a trans block. For example, the internationalized version of "Hello World" is "{% raw %}{% trans %}Hello World{% endtrans %}{% endraw %}".

Variables in trans block can be added like normal template variables. For example "Hello {{ name }}"" will become "{% raw %}{% trans %}Hello {{ name }}{% endtrans %}{% endraw %}". Multiple variables can be used in the same trans block.

Translation packages (.pot files) can be downloaded via API, and then corresponding string files (.po) can be uploaded via API, which will trigger translated template variants to be generated.

## Get translation package (.pot file)


This call will fetch a .pot translation package for all templates that have been assigned the corresponding tag.

`GET /il8n/pot/(:tag)`

#### Params:

- tag       -- String will return a .pot file only for templates that have the corresponding tag. Tags are set in the [dashboard](https://www.sendwithus.com/#/emails)

### Examples

Fetch .pot for template with tag "international".

`GET /i18n/pot/international`

#### Sample Response:

```
    #, fuzzy
    msgid ""
    msgstr ""

    #, python-format
    msgid "Welcome to sendwithus, %(first_name)s!"
    msgstr ""

    msgid "Confirm your email"
    msgstr ""
```

The reponse is a valid .pot file.

## Post translated strings and .po files

Use this endpoint to POST a .zip file containing .po files. Each .po file should be named to match the locale it is intended for. See examples below for specifics.

`POST /il8n/po/(:tag)`

#### Params:

- tag       -- String of tag; templates with that tag applied will have a locale generated for each .po file in the .zip file

#### Request Body:

- .zip file


### Examples

Example .zip structure:

```
translations.zip
    en-US.po
    ja-JP.po
```

Post translations.zip for templates with tag "international".

`POST /i18n/po/international`

#### Sample Response:

```json
{}
```

## Sending translated templates

At send time, Sendwithus uses the _locale_ parameter in the Send API, and matches it against the template version for that locale. This is why .po files must have a filename that matches the locale.

For an example sending with a translated template, please see the [send api](https://www.sendwithus.com/docs/api#send) documentation.

## Locale Code Standards

We follow the IETF Language Tag standard which consists of a 2 character language code and a 2 character country code seperated by a hyphen.  Example: 'en-US' is the code for English (United States)

IETF Language Tags: http://en.wikipedia.org/wiki/IETF_language_tag

The prefix, in this case 'en', is a language code following the ISO 639-1 standard.

ISO 639-1: http://en.wikipedia.org/wiki/List_of_ISO_639-1_codes

The suffix, in this case 'US', is a country code following the ISO 3166-1 Alpha-2 standard.

ISO 3166-1 Alpha-2: http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2

The Locale codes that we currently support are as follows (Last updated: February 18, 2015):

```
    ar-SA => Arabic (Saudi Arabia)
    zh-CN => Chinese (China)
    zh-TW => Chinese (Taiwan)
    cs-CZ => Czech (Czech Republic)
    nl-NL => Dutch (Netherlands)
    en-US => English (United States)
    en-AU => English (Australia)
    en-CA => English (Canada)
    en-GB => English (Great Britain)
    fr-CA => French (Canada)
    fr-FR => French (France)
    de-DE => German (Germany)
    hu-HU => Italian (Italy)
    it-IT => Hungarian (Hungary)
    ja-JP => Japanese (Japan)
    ko-KR => Korean (Korea)
    no-NO => Norwegian (Norway)
    pl-PL => Polish (Poland)
    pt-BR => Portuguese (Brazil)
    ru-RU => Russian (Russia)
    tr-TR => Turkish (Turkey)
    es-ES => Spanish (Spain)
    es-MX => Spanish (Mexico)
    es-US => Spanish (United States)
    sv-SE => Swedish (Sweden)
    vi-VN => Vietnamese (Vietnam)
```
