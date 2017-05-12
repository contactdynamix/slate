# Errors

The Survey Dynamix API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Incorrectly formatted request. Check the API.
401 | Unauthorised -- Your API credentials are wrong or you do not have permission to access the requested resource
404 | Not Found -- The requested resource could not be found
405 | Method Not Allowed -- You tried to access an API endpoint with an invalid method
409 | Not Modified Due to Existing Record Conflict -- You may have tried to add or update a resource in a way that would conflict with an existing resource, or you may have tried to delete a resource that is not in a deletable state.
410 | Gone -- The requested resource has been deleted
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
