Templates API
=============

*NOTE* -- All parameters are manditory unless otherwise noted.

Creating a New Template (Done - Already Existed)
-----------------------

POST `/templates`

Params:
- html       -- The HTML body of the template
- name       -- The name of the template
- subject    -- The sbuject line of th template
- text (opt) -- The Text body of the template

Creating a New Template Version (Done - Needs tests)
-------------------------------

POST `/templates/(:template_id)/versions`

Params:
- html       -- The HTML body of the template
- name       -- The name of the template
- subject    -- The sbuject line of th template
- text (opt) -- The Text body of the template

*NOTE* -- One of html or text must be specified

Updating a Template Version (Done - Needs tests)
---------------------------

PUT `/templates/(:template_id)/versions/(:version_id)`

Params:
- html       -- The HTML body of the template
- name       -- The name of the template
- subject    -- The sbuject line of th template
- text (opt) -- The Text body of the template

*NOTE* -- One of html or text must be specified
*NOTE* -- This will replace the current template version
