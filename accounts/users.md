Users
======

An Users is an entity used for basic login and management of the portal.

Properties
----------

| Property       | Explanation                                                                                      |
| -------------- | ------------------------------------------------------------------------------------------------ |
| id             | The unique numeric identifier for the user                                                   |
| name           | Name of the user                      |
| email          | Email of the user      |


Endpoints
---------

### GET /get_user

Receive a list of all users.


| Parameter      | Explanation                                                                                      |
| -------------- | ------------------------------------------------------------------------------------------------ |
| total_results  | total results found.                                                       |
| name           | Name for looking up.                                                       |
| email          | Email for looking up.                                                       |
| case           | if set to `True`, the search using the field `name` or `email` will be case-sensitive                                                                   |


#### GET /get_user

`HTTP/1.1 200 OK`

```json
{
    "total_results": 4,
    "user_list": [
        {
            "email": "bgcreative@mail.com",
            "id": 1886,
            "name": "bruno"
        },
        {
            "email": "dfdfd@sdsd.com",
            "id": 4328,
            "name": "bruno"
        },
        {
            "email": "sdfsf@ddfsdf.com",
            "id": 4330,
            "name": "bruno"
        },
        {
            "email": "have.host@yahoo.com.br",
            "id": 4422,
            "name": "bruno"
        }
    ]
}
```

### GET /categories/#{id}

Receive a single user. If there is not a user with the id, it will return a `500` error.

| Parameter      | Explanation                                                                                      |
| -------------- | ------------------------------------------------------------------------------------------------ |
| id             | the id of the user you want to get.                                        |

#### GET /categories/4567

`HTTP/1.1 200 OK`

```json
{
    "total_results": 1,
    "user_list": [
        {
            "email": "have.host@yahoo.com.br",
            "id": 4422,
            "name": "bruno"
        }
    ]
}
```

`HTTP/1.1 500 error`

```json
{
    "message": "internal server error.",
    "details": "user does not exist.",
}
```