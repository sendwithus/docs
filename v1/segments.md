Segments API
=============

*NOTE* -- All parameters are mandatory unless otherwise noted.

Send to a Segment (Done)
-----------------------

POST `/segments/(:segment_id)/send`

Params:

- email_id       -- ID of the template to send
- email_data (opt)       -- Key/Value data to merge into template
