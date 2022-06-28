# Posts



## Get All Posts
```shell
curl "{{host}}/posts" \
  -H "Authorization: yourJwtToken"
```

```json
The above command returns JSON structured like this:
{
  {
    "id": 1,
    "title": "Omnis et provident ad at.",
    "description": "Id omnis et animi volupsuscipit. Quae ad accusantium dicta.",
    "status": 0,
    "user_id": 1,
    "view_no": 0,
    "like_no": 1,
    "bookmark_no": 1,
    "comment_no": 0,
    "created_at": "2022-06-01T10:33:21.000000Z",
    "updated_at": "2022-06-01T10:33:35.000000Z"
  },
  {
    "id": 2,
    "title": "Fugit et dolor minima.",
    "description": "Non rem officiis assume voluptatem.",
    "status": 1,
    "user_id": 2,
    "view_no": 0,
    "like_no": 0,
    "bookmark_no": 3,
    "comment_no": 0,
    "created_at": "2022-06-01T10:33:21.000000Z",
    "updated_at": "2022-06-01T10:33:35.000000Z"
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

`GET http://localhost:8000/api/posts`


<aside class="notice">
Pagination — posts are shown in pagin mode, so for show next page you have to add ?page={next_page_no}
to the end of url
</aside>




## Get a Specific Post

```shell
curl "{{host}}/posts/<ID>" \
  -H "Authorization: yourJwtToken"
```


```json
if your request was correct, You will see successfull response just like the following:
{
    "post": {
        "id": 4,
        "title": "Eos quia unde accusantium.",
        "description": "Est occaecati queius qui officiis. Et architecto eius suscipit distinctio laboriosam exercitationem.",
        "status": 0,
        "user_id": 1,
        "view_no": 1,
        "like_no": 1,
        "bookmark_no": 1,
        "comment_no": 0,
        "created_at": "2022-06-01T10:33:21.000000Z",
        "updated_at": "2022-06-01T10:33:36.000000Z"
    }
}
```

```json-doc
if you aren't authenticated or you want to see not exist post, You will see responses like the following:
{
    "message": "Unauthenticated."
}
or
{
    "message": "No query results for model [App\\Models\\Post] 123",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\NotFoundHttpException",
}
# the above error show that the post you want to see is not exist.
```

### HTTP Request

`GET http://localhost:8000/api/posts/4`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to show




## Create a New Post

```shell
curl -X POST "{{host}}/posts" \
     -H "Accept: application/json"
     -H "Authorization: yourJwtToken"
     -d "title=postTitle&
        description=postDesc&
        status=postStatus"
```

```json
The above command returns JSON structured like this:
{
    "message": "post created seccessfully",
    "post": {
        "title": "a random title",
        "description": "whatever you like as a description",
        "status": "0",
        "user_id": 1,
        "updated_at": "2022-06-26T12:06:18.000000Z",
        "created_at": "2022-06-26T12:06:18.000000Z",
        "id": 23
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
    "message": "The title field is required. (and 1 more error)",
    "errors": {
        "title": [
            "The title field is required."
        ],
        "description": [
            "The description must be between 20 and 1502 characters."
        ]
    }
}
# you revieve recent response when you put incorrect form data in your request body!
```

### HTTP Request

`POST http://localhost:8000/api/posts`

### Form Data

name | Description
--------- | -----------
title | post title is requered and must be at least 5 char.
description | post desc is requered and must be at least 20 char.
status | post status is requered and show the activation of the post




## Update a Specific Post

```shell
curl -X PUT/PATCH "{{host}}/posts/<ID>" \
     -H "Accept: application/json"
     -H "Authorization: yourJwtToken"
     -d "at least one of the requered field that listed below"
```

```json
The above command returns JSON structured like this:
{
    "message": "post updated seccessfully",
    "post": {
        "id": 3,
        "title": "a clear and obvious title",
        "description": "whatever you like as description",
        "status": "1",
        "user_id": 1,
        "view_no": 1,
        "like_no": 0,
        "bookmark_no": 2,
        "comment_no": 0,
        "created_at": "2022-06-01T10:33:21.000000Z",
        "updated_at": "2022-06-26T10:20:16.000000Z"
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
    "message": "No query results for model [App\\Models\\Post] 123",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\NotFoundHttpException",
}
# the above error show that the post you want to see is not exist.
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

`PUT http://localhost:8000/api/posts/4`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to update

### The List of updatable field that can be present in Form Data in body

name of field |
--------- |
title |
description |
status |

<aside class="notice">
you can update any item of above list but you can't update non of above, in other hand at least on item of above list must be present in body section of your request.
</aside>




## Delete a Specific Post

```shell
curl -X DELETE "{{host}}/posts/<ID>" \
     -H "Accept: application/json"
     -H "Authorization: yourJwtToken"
```

```json
The above command returns JSON structured like this:
{
    "message": "post deleted seccessfully",
    "post": {
        "id": 3,
        "title": "a clear and obvious title",
        "description": "whatever you like as description",
        "status": 1,
        "user_id": 1,
        "view_no": 1,
        "like_no": 0,
        "bookmark_no": 2,
        "comment_no": 0,
        "created_at": "2022-06-01T10:33:21.000000Z",
        "updated_at": "2022-06-26T10:20:16.000000Z"
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
    "message": "No query results for model [App\\Models\\Post] 124",
    "exception": "Symfony\\Component\\HttpKernel\\Exception\\NotFoundHttpException",
}
# the above error show that the post you want to see is not exist.
```

### HTTP Request

`DELETE http://localhost:8000/api/posts/4`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to delete