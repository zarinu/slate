# Authentication
Please always be an authenticated user!
## Register

```shell
To sign up, use this code:
curl "{{host}}/auth/register" \
     -H "Accept: application/json"
     -d "first_name=yourName&
        last_name=yourName&
        email=yourEmail&
        role_id=yourRole&
        password=yourPass&
        password_confirmation=yourPass"
```


```json
if your request was correct, You will see successfull response just like the following::
{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRw",
    "token_type": "bearer",
    "expires_in": 420,
    "user": {
        "id": 7,
        "first_name": "zahra",
        "last_name": "heydari",
        "role_id": 4,
        "email": "zahira@gmail.com",
        "email_verified_at": null,
        "username": null,
        "date_of_birth": null,
        "gender": null,
        "mobile_no": null,
        "profile_image": null,
        "created_at": "2022-06-26T06:57:48.000000Z",
        "updated_at": "2022-06-26T06:57:48.000000Z"
    }
}
```


```json-doc
if your request invalid, You will see response with error same as the following::
{
    "message": "The last name must be between 3 and 50 characters. (and 7 more errors)",
    "errors": {
        "last_name": [
            "The last name must be between 3 and 50 characters."
        ],
        "email": [
            "The email has already been taken."
        ],
        "role_id": [
            "The role id must be between 1 and 4."
        ],
        "password": [
            "The password confirmation does not match.",
            "The password must be at least 8 characters.",
            "The password must contain at least one uppercase and one lowercase letter.",
            "The password must contain at least one symbol.",
            "The password must contain at least one number."
        ]
    }
}
```

InternshipProject uses JWT token to allow access to the API. You can register as a new user in our API and then get a JWT key.  

### HTTP Request

`POST http://localhost:8000/api/auth/register`

### Form Data

name | Description
--------- | -----------
role_id | the id of your role, for example writer: 2 or comment-manager:3 or a simpe user:4!

<aside class="notice">
if you don't know what you should enter as role_id, fill the value of this param with number 4, which is the role_id of a simple user.
</aside>


## Login

```shell
To login, use this code:
curl "{{host}}/auth/login" \
     -H "Accept: application/json"
     -d "email=yourEmail&
        password=yourPass"
```

```json
if your request was correct, You will see successfull response just like the following::
{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJo",
    "token_type": "bearer",
    "expires_in": 420,
    "user": {
        "id": 1,
        "first_name": "farzane",
        "last_name": "karimi",
        "role_id": 1,
        "email": "admin@gmail.com",
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
if your request invalid, You will see response with error same as the following::
{
    "message": "The email must be a valid email address. (and 1 more error)",
    "errors": {
        "email": [
            "The email must be a valid email address."
        ],
        "password": [
            "The password must be at least 8 characters."
        ]
    }
}
or
{
    "error": "NotAuthorizedException",
    "message": "Incorrect username or password"
}
```

if you have already registered, use login web service for login and get a JWT token with your personal information.

### HTTP Request

`POST http://localhost:8000/api/auth/login`

<aside class="warning">
Please remember to add <code>Accept: application/json</code> in your login and register and logout request header, to see the validation errors correctly.
</aside>

## Logout

```shell
# With shell, you can just pass the correct header with each request
To logout, use this code:
curl -X POST "{{host}}/auth/logout" \
     -H "Accept: application/json"
     -H "Authorization: Bearer yourJwtToken"
```

```json
if your request was correct, You will see successfull response just like the following:
{
    "message": "Successfully logged out"
}
```

```json-doc
if you aren't authenticated, You will see response like the following:
{
    "message": "Unauthenticated."
}
```

you can use our logout web service for discredit your JWT token and prevent possible abuse.

### HTTP Request

`POST http://localhost:8000/api/auth/logout`