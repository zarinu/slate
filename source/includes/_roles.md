# Roles



## Get All Roles
```shell
curl "{{host}}/admin/roles" \
  -H "Authorization: yourJwtToken"
```

```json
The above command returns JSON structured like this:
{
    "roles": [
        {
            "id": 1,
            "name": "سوپر ادمین",
            "en_name": "Superadmin",
            "description": "access all parts",
            "parent_id": null,
            "created_at": "2022-06-01T10:33:17.000000Z",
            "updated_at": "2022-06-01T10:33:17.000000Z"
        },
        {
            "id": 2,
            "name": "نویسنده",
            "en_name": "Writer",
            "description": null,
            "parent_id": 1,
            "created_at": "2022-06-01T10:33:17.000000Z",
            "updated_at": "2022-06-01T10:33:17.000000Z"
        }
    ]
}
```

```json-doc
if you aren't authenticated, You will see responses like the following:
{
    "message": "Unauthenticated."
}
```

### HTTP Request

`GET http://localhost:8000/api/roles`


<aside class="notice">
Pagination — Roles are shown in pagin mode, so for show next page you have to add ?page={next_page_no}
to the end of url
</aside>




## Get a Specific Role

```shell
curl "{{host}}/admin/roles/<ID>" \
  -H "Authorization: yourJwtToken"
```


```json
if your request was correct, You will see successfull response just like the following:
{
    "role": {
        "id": 3,
        "name": "مدیر کامنتها",
        "en_name": "Comment Manager",
        "description": null,
        "parent_id": 1,
        "created_at": "2022-06-01T10:33:18.000000Z",
        "updated_at": "2022-06-01T10:33:18.000000Z"
    }
}
```

```json-doc
if you aren't authenticated or you want to see not exist Role, You will see responses like the following:
{
    "message": "Unauthenticated."
}
or
{
    "message": "No query results for model [App\\Models\\Role] 123",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\NotFoundHttpException",
}
# the above error show that the Role you want to see is not exist.
```

### HTTP Request

`GET http://localhost:8000/api/admin/roles/4`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the Role to show




## Create a New Role

```shell
curl -X POST "{{host}}/roles" \
     -H "Accept: application/json"
     -H "Authorization: yourJwtToken"
     -d "name=ssth&
        en_name=sth&
        parent_id=sth"
```

```json
The above command returns JSON structured like this:
{
    "message": "role created seccessfully",
    "role": {
        "name": "ی چیزی برا تست",
        "en_name": "something as english name",
        "parent_id": "2",
        "updated_at": "2022-06-26T12:53:49.000000Z",
        "created_at": "2022-06-26T12:53:49.000000Z",
        "id": 5
    }
}
```

```json-doc
if you aren't authenticated or authorized or put invalid fields in body, You will see responses like the following:
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
    "message": "The name field is required. (and 1 more error)",
    "errors": {
        "name": [
            "The name field is required."
        ],
        "en_name": [
            "The en name field is required.",
            "The en name has already been taken."
        ]
    }
}
# you revieve recent response when you put incorrect form data in your request body!
```

### HTTP Request

`POST http://localhost:8000/api/admin/roles`

### Form Data

name | Description
--------- | -----------
name | role name and requered
en_name | role english name and requered
parent_id | the head of this new role and requered




## Update a Specific Role

```shell
curl -X PUT/PATCH "{{host}}/admin/roles/<ID>" \
     -H "Accept: application/json"
     -H "Authorization: yourJwtToken"
     -d "at least one of the requered field that listed below"
```

```json
The above command returns JSON structured like this:
{
    "message": "role updated seccessfully",
    "role": {
        "id": 2,
        "name": "ی چیزی برا تستنی",
        "en_name": "something as english namels",
        "description": null,
        "parent_id": "2",
        "created_at": "2022-06-01T10:33:17.000000Z",
        "updated_at": "2022-06-26T13:07:10.000000Z"
    }
}
```

```json-doc
if you aren't authenticated or authorized or you want to see a non existed Role or you have some validation error with form data, You will see responses like the following:
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
    "message": "No query results for model [App\\Models\\Role] 123",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\NotFoundHttpException",
}
# the above error show that the Role you want to see is not exist.
or
{
    "message": "The name has already been taken. (and 2 more errors)",
    "errors": {
        "name": [
            "The name has already been taken."
        ],
        "en_name": [
            "The en name has already been taken."
        ],
        "parent_id": [
            "The parent id must be between 1 and 5."
        ]
    }
}
```

### HTTP Request

`PUT http://localhost:8000/api/admin/roles/4`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the Role to update

### The List of updatable field that can be present in Form Data in body

name of field |
--------- |
name |
en_name |
parent_id |

<aside class="notice">
you can update any item of above list but you can't update non of above, in other hand at least on item of above list must be present in body section of your request.
</aside>




## Delete a Specific Role

```shell
curl -X DELETE "{{host}}/admin/roles/<ID>" \
     -H "Accept: application/json"
     -H "Authorization: yourJwtToken"
```

```json
The above command returns JSON structured like this:
{
    "message": "role deleted seccessfully",
    "role": {
        "id": 4,
        "name": "کاربر ساده",
        "en_name": "Simple User",
        "description": "has minimum access",
        "parent_id": 2,
        "created_at": "2022-06-01T10:33:18.000000Z",
        "updated_at": "2022-06-01T10:33:18.000000Z"
    }
}
```

```json-doc
if you aren't authenticated or authorized or you want to see a non existed Role, You will see responses like the following:
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
    "message": "No query results for model [App\\Models\\Role] 124",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\NotFoundHttpException",
}
# the above error show that the Role you want to see is not exist.
```

### HTTP Request

`DELETE http://localhost:8000/api/admin/roles/4`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the Role to delete