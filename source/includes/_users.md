# Users

## Description

> User resources follow this example format in JSON

```json
{
    "name": "Joe Smith",
    "email": "joesmith@example.com",
    "agent_id": "jSmith1",
    "phone": "+61499999999",
    "timezone": "Australia/Brisbane"
}
```

A user resource details the core properties of a survey dynamix user.

The users query API can be used to get detailed information about users for third party reporting or API interaction creation.

Each user resource contains the following information:

* The user’s email address which serves as their unique identifier

* The user’s name

* The user’s agent ID

* The user’s phone number

* The user’s timezone


<aside class="notice"> User resources are read only. </aside>


## Get Users List

> This code will return a JSON array of all users with "Joe" in their name associated with the authenticated customer:

```shell
curl -X GET   "https://surveydynamix.com/api/users?_limit=1000&name_contains=Joe" \
    -u Customer_UUID:Auth_Token
```

Gets a list of user resources associated with the authenticated customer.

### URI
`/users`

### Method
`GET`

### Parameters

| Name 	| Description 	| Allowed Values 	| Default 	|
|-------------------	|------------------------------------------------------------------------	|------------------------------	|---------	|
| _limit 	| The number of matching results to return. 	| integer between 1 and 1000 	| 10 	|
| _offset 	| The row number to start at if more than _limit results are found. 	| integer 	| 0 	|
| _order 	| The order of ID that results should be returned in. 	| ‘ASC’: earliest first 	| DESC 	|
|  	|  	| or ‘DESC’: most recent first 	|  	|
| name 	| The exact name of the user you want to find 	| string 	| none 	|
| name_contains 	| Part of the name of the user you want to find 	| string 	| none 	|
| agent_id 	| The agent ID of the user you want to find 	| string 	| none 	|
| phone 	| The phone number of the user you want to find 	| string 	| none 	|
| email 	| The email address of the user you want to find 	| string 	| none 	|



## Get Specific User

> This code will return a JSON object for the user with the email address joesmith@example.com:

```shell
curl -X GET   "https://surveydynamix.com/api/users/joesmith@example.com" \
    -u Customer_UUID:Auth_Token
```

Returns the JSON object for a user resource specified by `{email_address}`.

### URI
`/users/{email_address}`

### Method
`GET`

### Parameters
None




## Get Interactions List By User

> This code will return a JSON array of interaction resources associated with the user with email address joesmith@example.com:

```shell
curl -X GET   "https://surveydynamix.com/api/users/joesmith@example.com/interactions" \
    -u Customer_UUID:Auth_Token
```

Gets a list of interactions associated with a user by agent id

This works the same as a GET call to the /interactions resource with the `agent_id` parameter set to the selected user’s agent ID.

### URI
`/users/{email_address}/interactions`

###
GET

### Parameters
See [Get Interactions List](#get-interactions-list)
