# Overview

The sendwithus API is based on the REST paradigm, and thus features resource based URLs with standard HTTP response codes to indicate errors.  We use standard HTTP authentication and request verbs, and all responses are JSON formatted.

To make the integration process as easy as possible, we include test API keys with all accounts.  Any requests made with test API keys will handle data and give responses, but not actually send any emails.

### Base URL

All API URLs referenced in this document are relative to the following base URL:

```
https://api.sendwithus.com/v1
```
