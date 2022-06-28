---
title: IP

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - json
  - json-doc

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - authentication
  - users
  - posts
  - comments
  - roles
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the IP API
---

# Introduction

Welcome to the Internship Project API! You can use our API to access IP API endpoints, which can get information on users, posts, roles, and etc in our database.

We have language bindings in Shell, Json and Json-doc! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.
but in our API, we put codes related to sending a http request only in `Shell` language, and successfull response in `Json` and the response with error in the `Json-doc` languages.

For use this API in your local environment follow these steps:

1. `git clone https://git.aminsoft.org/aminsoft/internship-projects/web-projects/project_1_heydari/backend.git`

2. `cd backend && php artisan serve`

<aside class="success">
InternshipProject expects for the API jwt token to be included in all API requests to the server except `login` and `register` in a header that looks like the following:

<br><code>Authorization: Bearer yourJwtToken</code>
</aside>