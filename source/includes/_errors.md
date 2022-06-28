# Errors

The InternshipProject API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your JWT or credentials is wrong.
403 | Forbidden -- The users, posts or roles requested is hidden for administrators only; or maybe This action is unauthorized.
404 | Not Found -- The specified post, role or user could not be found.
406 | Not Acceptable -- You requested a format that isn't json.
410 | Gone -- The post, role or user requested has been removed from our servers.
422 | Unprocessable Content -- you have validations errors.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
