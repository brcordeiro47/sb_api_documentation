Site Blindado API Documentation
====================

This is a REST-style API that uses JSON for serialization and OAuth 2 for authentication.

Where do I start?
----------------

Want to get started with API integration? Here's a quick check list:

1. Register as a partner in [TODO](TODO).
2. Read up on [how to authenticate](#authentication) to learn how to make api calls.
3. Read the API docs to understand what you can do with your app.

Making a request
----------------

All URLs start with `http://localhost:8000/{partner_id}`.

So if your partner id number is 123456, your API url will be `http://localhost:8000/123456`.

To make a request for all the users you would do the following in curl:

```shell
curl -i -H 'content-type: application/json' -H 'accept: application/json' \
  --user ACCESS_TOKEN:x http://localhost:8000/123456/get_user
```

where `ACCESS_TOKEN` is the store's access token for your app (see Authentication).


Authentication
--------------

We follow the OAuth 2 framework for letting users authorize your application to use our API on their behalf. Quite briefly, when a user register as a partner you will obtain an access token (a secret string denoting your rights over his store), which you have to include in the header of every request (as shown in the above example).

Read the [authentication guide](TODO) to get started.


Just JSON
-----------------

All data is sent and received as JSON. Our format is to have no root element and we use snake\_case to describe attribute keys. This means that you have to send `Content-Type: application/json` when POSTing or PUTing data into our API.

You'll receive a `415 Unsupported Media Type` response code if you leave out the `Content-Type` header.


Client errors
-------------

These are the possible types of client errors on API calls that receive request bodies:

* Sending invalid JSON will result in a `400 Bad Request` response.

```
HTTP/1.1 400 Bad Request
Content-Length: 34

{"error": "Problems parsing JSON"}
```

* Sending invalid fields will result in a `422 Unprocessable Entity` response.

```
HTTP/1.1 422 Unprocessable Entity
Content-Length: 47

{
  "src": [
      "can't be blank"
    ]
}
```

Server errors
-------------

If Site Blindado is having trouble, you might see a 5xx error. `500` means that the app is entirely down, but you might also see `502 Bad Gateway`, `503 Service Unavailable`, or `504 Gateway Timeout`. It's your responsibility in all of these cases to retry your request later.


API resources
-----------------

* [Users](https://github.com/brcordeiro47/sb_api_documentation/accounts/user.md)


Help us make it better
----------------------

Please tell us how we can make the API better. If you have a specific feature request or if you found a bug, please use GitHub issues. Feel free to fork these docs and send a pull request with improvements.

To talk with us about the API, feel free to write to <mailto:dev@siteblindado.com.br>.