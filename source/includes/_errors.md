# Errors

The Survey Dynamix API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Incorrectly formatted request. Check the API.
401 | Unauthorized -- Your API credentials are wrong or you do not have permission to access the requested resource
404 | Not Found -- The requested resource could not be found
405 | Method Not Allowed -- You tried to access a kitten with an invalid method
410 | Gone -- The requested resource has been deleted
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
