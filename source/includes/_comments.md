# Comments



## Get All Comments
```shell
curl "{{host}}/posts/<ID>/comments" \
  -H "Authorization: yourJwtToken"
```

```json
The above command returns JSON structured like this:
{
    "comments": {
        "current_page": 1,
        "data": [
            {
                "id": 13,
                "body": "Suscipit molestiae consequuntur voluptate.",
                "status": 0,
                "user_id": 1,
                "post_id": 5,
                "created_at": "2022-06-01T10:33:25.000000Z",
                "updated_at": "2022-06-01T10:33:25.000000Z"
            },
            {
                "id": 21,
                "body": "lalaskldf",
                "status": 1,
                "user_id": 1,
                "post_id": 5,
                "created_at": "2022-06-27T05:12:16.000000Z",
                "updated_at": "2022-06-27T05:12:16.000000Z"
            }
        ],
        "first_page_url": "http://127.0.0.1:8000/api/posts/5/comments?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "http://127.0.0.1:8000/api/posts/5/comments?page=1",
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "http://127.0.0.1:8000/api/posts/5/comments?page=1",
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
        "path": "http://127.0.0.1:8000/api/posts/5/comments",
        "per_page": 10,
        "prev_page_url": null,
        "to": 2,
        "total": 2
    }
}
```

```json-doc
if you aren't authenticated, You will see responses like the following:
{
    "message": "Unauthenticated."
}
```

### HTTP Request

`GET http://localhost:8000/api/posts/5/comments`


<aside class="notice">
Pagination — Comments are shown in pagin mode, so for show next page you have to add ?page={next_page_no}
to the end of url
</aside>




## Create a New Comment

```shell
curl -X POST "{{host}}/posts/<ID>/comments" \
     -H "Accept: application/json"
     -H "Authorization: yourJwtToken"
     -d "body=postTitle&
        status=Commentstatus"
```

```json
The above command returns JSON structured like this:
{
    "message": "comment created seccessfully"
}
```

```json-doc
if you aren't authenticated, You will see responses like the following:
{
    "message": "Unauthenticated."
}
or
{
    "message": "The title field is required.",
    "errors": {
        "title": [
            "The title field is required."
        ],
    }
}
or
{
    "message": "No query results for model [App\\Models\\Post] 124",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\NotFoundHttpException",
}
# the above error show that the post you want to see its comments, not exist.
```

### HTTP Request

`POST http://localhost:8000/api/posts/5/comments`

### Form Data

name | Description
--------- | -----------
title | post title is requered and must be at least 5 char.
status | post status is requered and show the activation of the comment




## Update a Specific Post

```shell
curl -X PUT/PATCH "{{host}}/Comments/<ID>" \
     -H "Accept: application/json"
     -H "Authorization: yourJwtToken"
     -d "at least one of the requered field that listed below"
```

```json
The above command returns JSON structured like this:
{
    "message": "comment updated seccessfully",
    "comment": {
        "id": 6,
        "body": "lalaskldf",
        "status": "1",
        "user_id": 3,
        "post_id": 6,
        "created_at": "2022-06-01T10:33:24.000000Z",
        "updated_at": "2022-06-27T05:22:39.000000Z"
    }
}
```

```json-doc
if you aren't authenticated or authorized or you want to see a non existed post or you have some validation error with form data, You will see responses like the following:
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
    "message": "No query results for model [App\\Models\\Comment] 123",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\NotFoundHttpException",
}
# the above error show that the comment you want to see is not exist.
or
{
    "message": "The title field is required when none of description / status are present.",
    "errors": {
        "title": [
            "The title field is required when none of description / status are present."
        ]
    }
}
```

### HTTP Request

`PUT http://localhost:8000/api/Comments/6`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the comment to update

### The List of updatable field that can be present in Form Data in body

name of field |
--------- |
title |
status |

<aside class="notice">
you can update any item of above list but you can't update non of above, in other hand at least on item of above list must be present in body section of your request.
</aside>




## Delete a Specific Post

```shell
curl -X DELETE "{{host}}/Comments/<ID>" \
     -H "Accept: application/json"
     -H "Authorization: yourJwtToken"
```

```json
The above command returns JSON structured like this:
{
    "message": "comment deleted seccessfully",
    "comment": {
        "id": 6,
        "body": "lalaskldf",
        "status": "1",
        "user_id": 3,
        "post_id": 6,
        "created_at": "2022-06-01T10:33:24.000000Z",
        "updated_at": "2022-06-27T05:22:39.000000Z"
    }
}
```

```json-doc
if you aren't authenticated or authorized or you want to see a non existed post, You will see responses like the following:
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
    "message": "No query results for model [App\\Models\\Comment] 124",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\NotFoundHttpException",
}
# the above error show that the comment you want to see is not exist.
```

### HTTP Request

`DELETE http://localhost:8000/api/Comments/4`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the comment to delete