---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the IP API
---

# Introduction

Welcome to the Internship Project API! You can use our API to access IP API endpoints, which can get information on users, roles, and etc in our database.

We have language bindings just in Shell! You can view code examples in the dark area to the right, and you can't switch the programming language of the examples with the tabs in the top right.

For use this API in your local environment follow these steps:

1. `git clone https://git.aminsoft.org/aminsoft/internship-projects/web-projects/project_1_heydari/backend.git`

2. `cd backend && php artisan serve`


# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "localhost:8000/api/auth/me" \
  -H "Authorization: yourJwtToken"
```

InternshipProject uses API keys to allow access to the API. You can register a new IP API key by send a request to our [register url](localhost:8000/api/auth/register).  also if you have already registered, use our [login url](localhost:8000/api/auth/login) for get a new JWT token.

IP expects for the API jwt token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer yourJwtToken`

<aside class="notice">
for get a new JWT token You must send these data: <code>email, password, password_confirmation and name</code> (in register url) and these data: <code>email, password</code> (for login) with your request in body section.
</aside>