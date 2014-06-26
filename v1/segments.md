# Segments API

*NOTE* -- All parameters are mandatory unless otherwise noted.

## Send to a Segment

POST `/segments/(:segment_id)/send`

Params:

- email_id       -- ID of the template to send
- email_data (optional)       -- Key/Value data to merge into template
