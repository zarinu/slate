# Authentication

## Register
> To sign up, use this code:

```shell
curl "{{host}}/auth/register" \
     -d "first_name=yourName&
        last_name=yourName&
        email=yourEmail&
        role_id=yourRole&
        password=yourPass&
        password_confirmation=yourPass"
```

InternshipProject uses JWT token to allow access to the API. You can register as a new user in our API and then get a JWT key.  

<aside class="notice">
if you don't know what you should enter as role_id, fill the value of this param with number 4, which is the role_id of a simple user.
</aside>


## Login
> To login, use this code:

```shell
curl "{{host}}/auth/login" \
     -d "email=yourEmail&
        password=yourPass"
```

if you have already registered, use login web service for login and get a JWT token.


## Logout
> To logout, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl -X POST "{{host}}/auth/logout" \
     -H "Accept: aplication/json"
     -H "Authorization: Bearer yourJwtToken"
```

you can use our logout web service for discredit your JWT token and prevent possible abuse.

<aside class="success">
InternshipProject expects for the API jwt token to be included in all API requests to the server in a header that looks like the following:

<br><code>Authorization: Bearer yourJwtToken</code>
</aside>