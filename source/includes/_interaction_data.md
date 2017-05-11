# Interaction Data

## Description

> Interaction data resources follow this example format in JSON

```json
{
"id": 12214125,
"interaction_id": 24062,
"custom_key": "VALUE",
"custom_value": "GOLD",
"created_at": "2016-02-19 10:30:02",
"updated_at": "2016-02-19 10:30:02"
}
```

An interaction data resource details a custom key value pair associated with a specific survey interaction. These can be used to tag interactions with specific data for reporting purposes.

The API can be used to retrieve lists of Interaction Data objects related to a specific interaction or survey.

Interaction data objects contain the following information:

* A unique id

* The id of the associated interaction

* Custom key

* Custom value

* Timestamps describing when the key value pair was created and most recently updated.


## Get Interaction Data List

> This code will return a JSON array of interaction data resources associated with the interaction resource with ID = 891234:

```shell
curl -X GET   "https://surveydynamix.com/api/interaction_data?interaction_id=891234" \
    -u Customer_UUID:Auth_Token
```

> This code will return a JSON array containing just the interaction data object with custom key = foo for the interaction resource with ID = 891234:

```shell
curl -X GET   "https://surveydynamix.com/api/interaction_data?interaction_id=891234&custom_key=foo" \
    -u Customer_UUID:Auth_Token
```

Gets a list of interaction data resources associated with a survey or interaction resource.

At least one of `survey_id` or `interaction_id` must be specified.

### URI
`/interaction_data`

### Method
`GET`

### Parameters

| Name 	| Description 	| Allowed Values 	| Default 	|
|-------------------	|------------------------------------------------------------------------	|------------------------------	|---------	|
| survey_id 	| The ID of the survey resource the interaction data is associated with. 	| integer 	| none 	|
| interaction_id 	| The ID of the interaction resource the interaction data is associated with. 	| integer 	| none 	|
| _limit 	| The number of matching interaction data resources to return. 	| integer between 1 and 1000 	| 10 	|
| _offset 	| The row number to start at if more than _limit interaction data resources are found. 	| integer 	| 0 	|
| _order 	| The order of ID that results should be returned in. 	| ‘ASC’: earliest first 	| DESC 	|
|  	|  	| or ‘DESC’: most recent first 	|  	|
| custom_key 	| The custom key of the interaction data. 	| A string consisting only of alphanumeric characters and underscores and starting with a letter 	| none 	|



## Get Specific Interaction Data

> This code will return a JSON object for the interaction data resource with ID = 12214125:

```shell
curl -X GET   "https://surveydynamix.com/api/interaction_data/12214125" \
    -u Customer_UUID:Auth_Token
```

Returns the JSON object for an interaction data resource specified by `{interaction_data_id}`.

### URI
`/interaction_data/{interaction_data_id}`

### Method
`GET`

### Parameters
None


## Set Interaction Data

> This code will add the custom key value pair foo=bar to the interaction resource with ID = 891234:

```shell
curl -X POST   "https://surveydynamix.com/api/interaction_data" \
    -d "interaction_id=891234" \
    -d "custom_key=foo" \
    -d "custom_value=bar" \
    -u Customer_UUID:Auth_Token
```

> This code will update the existing custom key value pair to foo=baz:

```shell
curl -X POST   "https://surveydynamix.com/api/interaction_data" \
    -d "interaction_id=891234" \
    -d "custom_key=foo" \
    -d "custom_value=baz" \
    -u Customer_UUID:Auth_Token
```

Adds a custom key value pair associated with a specified interaction.

If the custom key already exists for that interaction, it is overwritten with the new value.

The updated interaction data JSON object will be returned.

### URI
`/interaction_data`

### Method
`POST`

### Parameters

| Name 	| Description 	| Allowed Values 	| Default 	|
|-------------------	|------------------------------------------------------------------------	|------------------------------	|---------	|
| interaction_id 	| The ID of the interaction resource the interaction data is associated with. 	| integer 	| Required 	|
| custom_key 	| The custom key of the interaction data. 	| A string consisting only of alphanumeric characters and underscores and starting with a letter 	| Required 	|
| custom_value 	| The custom value of the interaction data. 	| string	| Required 	|


## Delete Interaction Data

> This code will delete the interaction data resource with ID = 12214125:

```shell
curl -X DELETE   "https://surveydynamix.com/api/interaction_data/12214125" \
    -u Customer_UUID:Auth_Token
```

Deletes an interaction data resource specified by `{interaction_data_id}`.

### URI
`/interaction_data/{interaction_data_id}`

### Method
`DELETE`

### Parameters
None
