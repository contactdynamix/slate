---
title: API Reference

language_tabs:
  - shell
toc_footers:
  - <a href='https://surveydynamix.com'>Visit Survey Dynamix</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - interactions
  - errors

search: true
---

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Using the API

## Base URL

All API calls referenced in this document have the following base:

`https://surveydynamix.com/api`

To get the URL for an individual request, append the URI listed in the request details to the base URL.

The Survey Dynamix REST API is served over HTTPS. To ensure data privacy, unencrypted HTTP is not supported.

## Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the API credentials with each request
curl "api_endpoint_here"
  -u CustomerUUID:AuthToken
```

> Make sure to replace `CustomerUUID:AuthToken` with your specific api credentials.

All requests to this API use HTTP Basic Authentication. You will use your customer Uuid as the username and your generated auth token as the password.

You can find your customer authentication credentials on the customer settings page [here](https://surveydynamix.com/customer_settings#tab_customer-credentials)

username: `Customer Uuid`

password: `Auth Token`

Verification is also possible using the auth_token parameter for requests present in version 0.9 of the API to support backwards compatibility. However this system of authentication is deprecated and may not be supported in future versions.