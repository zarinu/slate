# Posts

## Get All Posts

```shell
curl "http://localhost:8000/api/posts" \
  -H "Authorization: yourJwtToken"
```

> The above command returns JSON structured like this:
```json
[
  {
    "id": 1,
    "title": "Omnis et provident ad at.",
    "description": "Id omnis et animi voluptatem qui. Animi ut delectus qui nihil et laudantium. Ducimus quasi qui et laborum eos ea asperiores. Natus accusamus nostrum qui. Adipisci quam magnam reiciendis tenetur corrupti aut suscipit. Quae ad accusantium dicta.",
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
    "description": "Non rem officiis assumenda odio numquam. Aut voluptates alias hic adipisci officia. Iure nisi laboriosam tempora commodi eum odit dolor. Non fugiat quo beatae. Ex recusandae a et aut neque voluptatem.",
    "status": 1,
    "user_id": 2,
    "view_no": 0,
    "like_no": 0,
    "bookmark_no": 3,
    "comment_no": 0,
    "created_at": "2022-06-01T10:33:21.000000Z",
    "updated_at": "2022-06-01T10:33:35.000000Z"
  }
]
```

This endpoint retrieves all posts.

### HTTP Request

`GET http://localhost:8000/api/posts`

<aside class="notice">
Pagination — posts are shown in pagin mode, so for show next page you have to add ?page={next_page_no}
to the end of url
</aside>

## Get a Specific Post

```shell
curl "http://localhost:8000/api/posts/<ID>" \
  -H "Authorization: yourJwtToken"
```

> The above command returns JSON structured like this:
```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific post.

### HTTP Request

`GET http://localhost:8000/posts/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to delete


## Create a New Post

```shell
curl "http://localhost:8000/posts" \
  -X POST \
  -H "Authorization: yourJwtToken"
```

> The above command returns JSON structured like this:
```json
{
  "message": "post created seccessfully",
  "post": {
      "id": 2,
      "other info": ...,
  }
}
```

This endpoint creates a new post.


## Update a Specific Post

```shell
curl "http://localhost:8000/posts/<ID>" \
  -X PUT or PATCH \
  -H "Authorization: yourJwtToken"
```

> The above command returns JSON structured like this:
```json
{
  "message": "post updated seccessfully",
  "post": {
      "id": 2,
      "other info": ...,
  }
}
```

This endpoint updates a specific post.

### HTTP Request

`PUT http://localhost:8000/posts/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to update

## Delete a Specific Post

```shell
curl "http://localhost:8000/posts/2" \
  -X DELETE \
  -H "Authorization: yourJwtToken"
```

> The above command returns JSON structured like this:
```json
{
  "message": "post deleted seccessfully",
  "post": {
      "id": 2,
      "other info": ...,
  }
}
```

This endpoint deletes a specific post.

### HTTP Request

`DELETE http://localhost:8000/posts/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to delete

