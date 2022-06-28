
# Users

InternshipProject expects `Accept Header` be included in all API requests that looks like the following:
`Accept: application/json`
<aside class="warning">
Accept Header - if you don't, you will probably receive incorrect responses in some cases!
</aside>




## Get All Users

```shell
curl "{{host}}/users" \
     -H "Accept: application/json"
     -H "Authorization: Bearer yourJwtToken"
```

```json
The above command returns JSON structured like this:
{
    "users": {
        "current_page": 1
        "data": [
            {
                "id": 1
                "first_name": "farzane"
                "last_name": "karimi"
                "role_id": 1
                "email": "admin@gmail.com"
                "email_verified_at": null
                "username": null
                "date_of_birth": null
                "gender": null
                "mobile_no": null
                "profile_image": null
                "created_at": "2022-06-01T10:33:18.000000Z"
                "updated_at": "2022-06-01T10:33:18.000000Z"
            }
            {
                "id": 2
                "first_name": "sosan"
                "last_name": "alishahi"
                "role_id": 2
                "email": "sosan@gmail.com"
                "email_verified_at": null
                "username": null
                "date_of_birth": null
                "gender": null
                "mobile_no": null
                "profile_image": null
                "created_at": "2022-06-01T10:33:18.000000Z"
                "updated_at": "2022-06-01T10:33:18.000000Z"
            }
        ],
        "first_page_url": "http://127.0.0.1:8000/api/users?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "http://127.0.0.1:8000/api/users?page=1",
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "http://127.0.0.1:8000/api/users?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "next_page_url": null,
        "path": "http://127.0.0.1:8000/api/users",
        "per_page": 8,
        "prev_page_url": null,
        "to": 2,
        "total": 2
    }
}
```

```json-doc
if you aren't authenticated or authorized, You will see responses like the following:
{
    "message": "Unauthenticated."
}
or 
{
    "message": "This action is unauthorized.",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\AccessDeniedHttpException",
    "file": "/home/mrs/FirstProject_Backend/vendor/laravel/framework/src/Illuminate/Foundation/Exceptions/Handler.php"
}
```

### HTTP Request

`GET http://localhost:8000/api/users`

<aside class="notice">
users are shown in pagination and in a specific numper per page, so for show next page you have to add <code>?page={next_page_no}</code>
at the end of url
</aside>




## Get a Specific User

```shell
curl "{{host}}/users/<ID>" \
     -H "Accept: application/json"
     -H "Authorization: Bearer yourJwtToken"
```

```json
if your request was correct, You will see successfull response just like the following:
{
    "user": {
        "id": 2,
        "first_name": "sosan",
        "last_name": "alishahi",
        "role_id": 2,
        "email": "sosan@gmail.com",
        "email_verified_at": null,
        "username": null,
        "date_of_birth": null,
        "gender": null,
        "mobile_no": null,
        "profile_image": null,
        "created_at": "2022-06-01T10:33:18.000000Z",
        "updated_at": "2022-06-01T10:33:18.000000Z"
    }
}
```

```json-doc
if you aren't authenticated or authorized, You will see responses like the following:
{
    "message": "Unauthenticated."
}
or 
{
    "message": "This action is unauthorized.",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\AccessDeniedHttpException",
    "file": "/home/mrs/FirstProject_Backend/vendor/laravel/framework/src/Illuminate/Foundation/Exceptions/Handler.php"
}
or
{
    "message": "No query results for model [App\\Models\\User] 123",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\NotFoundHttpException",
}
# the above error show that the user you want to see is not exist.
```

### HTTP Request

`GET http://localhost:8000/api/users/2`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to show




## Update a Specific User

```shell
curl -X PUT/PATCH  "{{host}}/users/<ID>" \
     -H "Accept: application/json"
     -H "Authorization: Bearer yourJwtToken"
     -d "at least on field must be present"
```

```json
if your request was correct, You will see successfull response just like the following:
{
    "message": "user updated seccessfully",
    "user": {
        "id": 2,
        "first_name": "solmaz",
        "last_name": "bandari",
        "role_id": 2,
        "email": "sosan@gmail.com",
        "email_verified_at": null,
        "username": null,
        "date_of_birth": "1999-12-03",
        "gender": null,
        "mobile_no": null,
        "profile_image": null,
        "created_at": "2022-06-01T10:33:18.000000Z",
        "updated_at": "2022-06-26T10:31:58.000000Z"
    }
}
```

```json-doc
if you aren't authenticated or authorized or haven't any field in your body to update, You will see responses with errors just like the following:
{
    "message": "Unauthenticated."
}
or 
{
    "message": "This action is unauthorized.",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\AccessDeniedHttpException",
    "file": "/home/mrs/FirstProject_Backend/vendor/laravel/framework/src/Illuminate/Foundation/Exceptions/Handler.php"
}
or
{
    "message": "The last name field is required when none of first name / username / email / role id / password / date of birth / mobile no / gender / profile image are present.",
    "errors": {
        "last_name": [
            "The last name field is required when none of first name / username / email / role id / password / date of birth / mobile no / gender / profile image are present."
        ]
    }
}
or
{
    "message": "No query results for model [App\\Models\\User] 123",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\NotFoundHttpException",
}
```

### HTTP Request

`PUT http://localhost:8000/api/users/2`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to update

### The List of updatable field that can be present in Form Data in body

name of field |
--------- |
first_name |
last_name |
username |
email |
role_id |
password |
date_of_birth |
mobile_no |
gender |
profile_image |

<aside class="notice">
you can update any item of above list but you can't update non of above, in other hand at least on item of above list must be present in body section of request.
</aside>




## Delete a Specific User

```shell
curl -X DELETE  "{{host}}/users/<ID>" \
     -H "Accept: application/json"
     -H "Authorization: Bearer yourJwtToken"
```

```json
if your request was correct, You will see successfull response just like the following:
{
    "message": "user deleted seccessfully",
    "user": {
        "id": 2,
        "first_name": "solmaz",
        "last_name": "bandari",
        "role_id": 2,
        "email": "sosan@gmail.com",
        "email_verified_at": null,
        "username": null,
        "date_of_birth": "1999-12-03",
        "gender": null,
        "mobile_no": null,
        "profile_image": null,
        "created_at": "2022-06-01T10:33:18.000000Z",
        "updated_at": "2022-06-26T10:31:58.000000Z"
    }
}
```

```json-doc
if you aren't authenticated or authorized or haven't any field in your body to update, You will see responses with errors just like the following:
{
    "message": "Unauthenticated."
}
or 
{
    "message": "This action is unauthorized.",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\AccessDeniedHttpException",
    "file": "/home/mrs/FirstProject_Backend/vendor/laravel/framework/src/Illuminate/Foundation/Exceptions/Handler.php"
}
or
{
    "message": "No query results for model [App\\Models\\User] 123",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\NotFoundHttpException",
}
```

### HTTP Request

`DELETE http://localhost:8000/api/users/2`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to update