Send API
=============

*NOTE* -- All parameters are mandatory unless otherwise noted.

Send an Email (Done)
-----------------------

POST `/send`

Params:

- email_id       -- Unique ID obtained from /emails
- recipient      
   - address -- The recipient's email address
   - name (opt) -- The recipient's name
- cc 		-- An array of CC recipients, of the format {"address":"cc@email.com"}
- bcc 		-- An array of BCC recipients, of the format {"address":"bcc@email.com"}
- sender (opt)
   - address 	-- The sender's email address
   - reply_to 	-- The sender's reply-to address
   - name 		-- The sender's name
- email_data 	-- Object containing email template data
- tags 			-- Array of tags (as strings)
- inline 		-- Inline attachment object (see example)
- files			-- List of file attachments (combined maximum 7MB, see example)
- esp_account 	-- ID of the ESP Account to send this email through. ex: esp_1a2b3c4d5e

Sample Request Body:
```json
{
  // Required parameters
  "email_id": "tem_A5RHVP6CnRbS34UysLjYHx",
  "recipient": {
    "name": "John",
    "address": "user@email.com"
  },
  "email_data": { "amount": "$12.00" },

  // Optional parameters
  "cc": [
    {"address": "cc_one@email.com"},
    {"address": "cc_two@email.com"}
  ],

  "bcc": [
    {"address": "bcc_one@email.com"},
    {"address": "bcc_two@email.com"}
  ],

  "sender": {
    "name": "Company",
    "address": "company@company.com",
    "reply_to": "info@company.com"
  },

  "tags": [
    "tag1",
    "tag2",
    "tag3"
  ],

  "inline": {
    "id": "cat.png",
    "data": "{BASE_64_ENCODED_FILE_DATA}"
  },

  "files": [
    {
      "id": "doc.txt",
      "data": "{BASE_64_ENCODED_FILE_DATA}"
    },
    {
      "id": "stuff.zip",
      "data": "{BASE_64_ENCODED_FILE_DATA}"
    }
  ],

  "esp_account": "esp_1a2b3c4d5e"
}

```

