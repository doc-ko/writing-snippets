# Introduction
The Foobar Pro™ API is an extension of the Foobar Pro™ product suite to manage the life cycle of credit, debit, and prepaid cards.

This document describes the available endpoints for debit, prepaid, and credit cards.
These endpoints integrate with an existing Foobar Pro™ platform to implement your services.
Note that implementing debit requires an interface with your banking system.

This document **does not describe** the installation and configuration of the Foobar Pro™ API.
Instead, refer to the following documentation:

* Foobar Pro™ REST API Configuration Technical Reference Guide (TRG)

Contact Acme Inc. to set up product offerings, or obtain access credentials.

**Note:** 
Foobar Pro™ API usage is not suitable for end-user applications. 
Its primary purpose is for integratation with system applications (backend).

## Intended Audience

This document is intended for backend developers and systems engineers who are familiar with:

* the Foobar Pro™ product suite
* REST APIs

# Overview

## Current Version
The current API Version is 1.
All requests to `{REDACTED_URL}` receive the `v1` version of the REST API. 

## Schema Representation
### Encoding
Data is sent and received in JSON format, using UTF-8 Encoding.
We recommend that you explicitly define the Accept header:

```
Accept: application/json
```

### Date format
Unless otherwise specified, the date format used in the requests and responses is `YYYY-MM-DD` (ISO-8601 compliant).

### Time format
Unless otherwise specified, the time format used in requests and responses is `hh:mm:ss`.

### Mandatory and Optional Fields
* Mandatory fields in requests are marked as _required_.

    * Some fields may become mandatory depending on the value of related fields.
      These cases are described in the field's definition.
    

* Any field not specified as mandatory is optional.

### Blank Field Responses
When receiving a response, blank fields are **not omitted**.
Instead, they are included as `null`.

```
{
    customer_nbr: 00001,
    credit: 999999,
    debit: null,
    debt: null
}
```
## Authentication
All users must be authenticated before they can access the API endpoints.
Contact Acme Inc. for an API key. All endpoints require Bearer authentication. 

Authentication must be sent in the Authorization Header, e.g.
```
curl {REDACTED_URL} -H "Accept: application/json" -H "Authorization: Bearer {API_KEY}"
```

## Error representation
In case of a processing error, REST APIs return an HTTP Status of `40X` or `500`, and a JSON body containing date and time, error number and message.
The error number is for Acme Inc. internal use: to investigate the cause of the error.
The message contains a description of the error.

There are six possible types of errors on API calls.

1. Sending invalid JSON:
    ```
    REDACTED
    ```
2. Sending invalid fields:
    ```
    REDACTED
    ```
3. Request an invalid resource
    ```
    REDACTED
    ```
4. Request made without or with an invalid API Key:
    ```
    REDACTED
    ```
5. Request made without sufficient privileges:
    ```
    REDACTED
    ```
6. Error in Foobar Pro™ processing (default error):
    ```
    REDACTED
    ```
    
## HTTP Methods allowed
The Foobar Pro™ API allows the following methods:

<table>
<tr><th>Method</th><th>Description</th></tr>
<tr><td>

`GET`

</td><td>Retrieve resource information</td></tr>
<tr><td>

`POST`

</td><td>Create a new resource</td></tr>
<tr><td>

`PUT`

</td><td>Update resource information</td></tr>
<tr><td>

`DELETE`

</td><td>Disable or remove a resource</td></tr>
</table>


