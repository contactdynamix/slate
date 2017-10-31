---
title: API Reference

language_tabs:
  - shell
toc_footers:
  - <a href='https://surveydynamix.com'>Visit Survey Dynamix</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - interactions
  - interaction_data
  - responses
  - surveys
  - questions
  - users
  - phone_numbers
  - errors

search: true
---

# Introduction

Welcome to the Survey Dynamix REST API Reference version 1.0.0

The Survey Dynamix API allows you to programmatically add survey interactions, retrieve results and even perform surveys via your own applications.

This page details all the API resources you will need to create powerful integrations with Survey Dynamix.

# Using the API

## Base URL

All API calls referenced in this document have the following base URL:

`https://surveydynamix.com/api`

To get the api endpoint for an individual request, append the URI listed in the request details to the base URL.

The Survey Dynamix REST API is served over HTTPS. To ensure data privacy, unencrypted HTTP is not supported.

## Authentication

### OAuth2
<aside class="warning">
Note: OAuth2 is temporarily unavailable as an authentication method. Use basic authentication instead.
</aside>

The Survey Dynamix API supports authorisation code grant and personal access token methods. This documentation assumes you are already familiar with OAuth2 grant flows.

### Authorisation Code Grant

> To authorise API calls using an Authorisation Code, use this code:

```shell
# Using an access token, pass the token as part of the authorisation header with each request
curl "api_endpoint_here" \
  -H "Authorization: Bearer {Token}"
```

> Make sure to replace `{Token}` with the access token.

Survey Dynamix users with admin privileges can create OAuth clients [here](https://surveydynamix.com/customer_settings#tab_integrations).

We use the standard OAuth2 authorisation code flow. To start, the client application must redirect the user to the Survey Dynamix authorisation endpoint at `http://surveydynamix.com/oauth/authorize`. The redirect must include the following parameters:

* `response_type`: This will be set to `code`.
* `client_id`: This is listed in the OAuth Clients table after you have created a client.
* `client_secret`: This is listed in the OAuth Clients table and should be kept secure.
* `redirect_uri`: This must match the redirect URL that was specified when creating the client and will be used for the callback endpoint when the user grants access.

Once the user has been redirected, they will be presented with a form allowing them to either approve or cancel the request. If the request is approved, the user will be redirected back to the redirect URL. This redirect will include a authorisation code.

To convert the authorisation code into an access token, the client application must make a final POST request to the access token endpoint at `http://surveydynamix.com/oauth/token` with the following parameters:

* `grant_type`: This will be set to `authorization_code`
* `client_id`, `client_secret`, & `redirect_uri`: These will be the same as in the authorisation redirect.
* `code`: Use the authorisation code included in the post-authorisation redirect.

This request will return a JSON response containing the `access_token` attribute.

To authenticate using an access token add an authorisation header to each request in the following format:

`Authorization: Bearer {access token}`


### Personal Access Tokens

> To authorise API calls using a Personal Access Token, use this code:

```shell
# Using personal access token auth, pass the token as part of the authorisation header with each request
curl "api_endpoint_here" \
  -H "Authorization: Bearer {Token}"
```

> Make sure to replace `{Token}` with your  personal access token.

Survey Dynamix users with admin privileges can create personal access tokens to authenticate API calls [here](https://surveydynamix.com/customer_settings#tab_integrations).

Personal access tokens are shown to the user *only once* upon creation and should be stored securely.

To authenticate using a personal access token add an authorisation header to each request in the following format:

`Authorization: Bearer {personal access token}`


### Basic Authentication

> To authorise API calls using Basic Authentication, use this code:

```shell
# Using Basic Auth, pass the default API credentials with each API call
curl "api_endpoint_here" \
  -u CustomerUUID:AuthToken
```

> Make sure to replace `CustomerUUID:AuthToken` with your specific api credentials.

Basic Authentication is the simplest authentication method that Survey Dynamix offers. You will use your customer Uuid as the username and your generated auth token as the password.

You can find your customer authentication credentials on the customer settings page [here](https://surveydynamix.com/customer_settings#tab_customer-credentials)

username: `Customer Uuid`

password: `Auth Token`