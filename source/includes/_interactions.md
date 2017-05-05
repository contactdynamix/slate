# Interactions
## Description

> Interaction resources follow this example format in JSON

```json
{
"id": 24062,
"uuid": "7aa870f0-046f-11e7-9cc9-9de741d6e753",
"survey_id": 493,
"phone_number": "+61409999999",
"email": "john.bloggs@example.com"
"survey_type": "inbound",
"scheduled_at": "2016-02-19 10:30:02",
"external_ref": "example-id-235i129",
"updated_at": "2016-02-19 10:30:02",
"created_at": "2016-02-19 10:30:02",
"call_type": "support",
"agent_id": "nevilr",
"status": "Not Started",
"web_link": "https://surveydynamix.com/web_survey/<uuid>"
}
```

An interaction resource represents a request for a survey respondent to complete a specified survey. The status of all interactions with survey respondents are tracked by the Survey Dynamix system using the interaction resource.
The interaction resource API is used to create new survey interactions, update existing interactions with new information, and view the status of existing interactions. Each interaction JSON object can contain any of the following information:

* A unique interaction ID

* The ID of the survey that the interaction belongs to

* The contact phone number that will be used to perform outbound voice or SMS interactions

* The email address of the survey respondent if the survey is a web survey distributed via email

* The survey type - the medium by which the interaction will be performed.

* A timestamp scheduling when the interaction should be performed by the Survey Dynamix system

* Timestamps specifying when the interaction was created and last updated

* The agent ID of a user in the Survey Dynamix system, used for report aggregation

* A text field describing the current status of the interaction at point of retrieval

* The web link that a respondent would follow to complete the survey

* The call type and external reference populated by the customer.



## Get Interactions List

> This code will return 5 outbound interactions from the survey with ID = 52:

```shell
curl -X GET   "https://surveydynamix.com/api/interactions?survey_id=52&_limit=5&survey_type=outbound" \
    -u Customer_UUID:Auth_Token
```
Gets a list of survey interactions as a JSON array of interaction resources.
### URI
`/interactions`
### Method
`GET`

### Parameters
| Name | Description | Allowed Values | Default
| --- | --- | --- | --- |
| survey_id | The ID of the survey the interactions belong to. Found on the top right of the relevant survey page. | integer | Required |
| _limit | The number of matching interactions to return. | integer between 1 and 1000 | 10 |
| _offset | The row number to start at if more than _limit interactions are found. | integer | 0 |
| _order | The order of ID that results should be returned in. | ‘ASC’: earliest first or ‘DESC’: most recent first  | Default order is by current interaction status. |
| _include_responses | Whether or not to include question responses in JSON. When true, response objects (see 3.2) will be appended in an array under the “responses” field. | boolean | FALSE |
| _include_data | Whether or not to include interaction data in JSON. When true, interaction data objects (see 4.2) will be appended in an array under the “interaction_data” field. | boolean | FALSE |
| email | The email address to be used in surveying. | An email address | empty |
| survey_type | The survey medium to use. | inbound, outbound, sms | none |
| scheduled_at | The exact time the interaction was scheduled for | dateTime | none |
| external_ref | A standard string field for referencing external system IDs. | string | none |
| call_type | A standard string field for report aggregation | string | none |
| agent_id | A string corresponding to an agent ID for report aggregation. | string | none |
| started | Whether or not the interaction has started | boolean | none |
| completed | Whether or not the interaction has completed | boolean | none |
| survey_ended | Whether or not the survey was successfully completed within the interaction | boolean | none |

## Add New Interaction

> This code will create an email interaction for respondent@example.com on survey with ID = 52 to be sent in 5 minutes:

```shell
curl -X POST   "https://surveydynamix.com/api/interactions" \
    -d "survey_id=52" \
    -d "survey_type=email" \
    -d "email=respondent@example.com" \
    -d "scheduled_at=Now + 5 minutes" \
    -u Customer_UUID:Auth_Token
```

Creates a survey interaction with the specified parameters.
### URI
`/interactions`
### Method
`POST`

### Parameters
| Name | Description | Allowed Values | Default
| --- | --- | --- | --- |
| survey_id | The ID of the survey you wish to add the interaction to. Found on the top right of the relevant survey page. | integer | Required |
| _force_new | Force a new interaction to be added even if a pending interaction with the same number and survey ID exists. | boolean | FALSE |
| phone_number | The phone number to be used in surveying. Required for voice and sms interactions. | A 12 character string in the proper phone number format | empty |
| email | The email address to be used in surveying. Required for email interactions. | An email address | empty |
| survey_type | The survey medium to use. | inbound, outbound, sms, web, email | web |
| scheduled_at | The time at which an outbound/sms survey will start, or the time after which an inbound survey is allowed to start. | dateTime string. Accepts times in standard UTC format and in the format “Now + X Days/Hours/Minutes” | now |
| external_ref | A standard string field for referencing external system IDs. | string | empty |
| call_type | A standard string field for report aggregation | string | empty |
| agent_id | A string corresponding to an agent ID. Will allow an agent user with this ID to see the interaction in the dashboard, and will be used to aggregate for agent rankings. | string | empty |
| Custom Metadata| parameters not otherwise listed in this table will be added as interaction data resources associated with the created interaction. | The key must only include alphanumeric characters and underscores and must start with a letter. The value may be any string. | none |

## Get Specific Interaction

> This code will return a JSON object for the interaction resource with ID = 891234:

```shell
curl -X GET   "https://surveydynamix.com/api/interactions/891234" \
    -u Customer_UUID:Auth_Token
```

Returns the JSON object for an interaction resource specified by `{interaction_id}`


### URI
`/interactions/{interaction_id}`
### Method
`POST`

### Parameters
| Name | Description | Allowed Values | Default
| --- | --- | --- | --- |
| _include_responses | Whether or not to include question responses in JSON. When true, response objects (see 3.2) will be appended in an array under the “responses” field. | boolean | FALSE |
| _include_data | Whether or not to include interaction data in JSON. When true, interaction data objects (see 4.2) will be appended in an array under the “interaction_data” field. | boolean | FALSE |


## Delete Interaction

> This code will delete the interaction resource with ID = 891234:

```shell
curl -X DELETE   "https://surveydynamix.com/api/interactions/891234" \
    -u Customer_UUID:Auth_Token
```

Deletes an interaction resource specified by `{interaction_id}`.

Note that for billing and data consistency purposes, interactions cannot be deleted once they have started.

### URI
`/interactions/{interaction_id}`
### Method
`DELETE`

### Parameters
None

## Update Interaction

> This code will update the interaction resource with ID = 891234 using a modified JSON object:

```shell
curl -X PUT   "https://surveydynamix.com/api/interactions/891234" \
    -d "interaction={\"id\":891234,\"survey_id\":52,\"phone_number\":\"\",\"survey_type\":\"email\",\"scheduled_at\":\"2017-05-04 02:53:49\",\"external_ref\":\"\",\"created_at\":\"2017-05-04 02:53:49\",\"updated_at\":\"2017-05-04 02:54:55\",\"call_type\":\"\",\"agent_id\":\"\",\"uuid\":\"e67fa4e0-3074-11e7-8efe-116b9b2f6833\",\"email\":\"rileyneville@gmail.com\",\"status\":\"Completed 1 hour ago\",\"weblink\":\"https:\/\/surveydynamix.com\/web_survey\/e67fa4e0-3074-11e7-8efe-116b9b2f6833\"}" \
    -u Customer_UUID:Auth_Token
```

Updates a specified interaction with new properties supplied in a JSON object.

Note that the new JSON object must have the same ID as the resource you are attempting to update.

### URI
`/interactions/{interaction_id}`
### Method
`PUT`

### Parameters
| Name | Description | Allowed Values | Default
| --- | --- | --- | --- |
| interaction | A JSON object representing the interaction in the same format as returned by get and create requests with the fields to update altered in text. | JSON String | Required |


## Get Responses List for Interaction

> This code will return a list of survey response resources associated with the interaction resource with ID = 891234:

```shell
curl -X GET   "https://surveydynamix.com/api/interactions/891234/responses" \
    -u Customer_UUID:Auth_Token
```

Gets a list of survey responses for the requested interaction.

This works the same as a GET call to the /responses resource with the interaction_id parameter set to `{interaction_id}``

### URI
`/interactions/{interaction_id}/responses`
### Method
`GET`

### Parameters
See [Get Responses List.](#get-responses-list)


## Get Interaction Data List for Interaction

> This code will return a list of interaction data resources associated with the interaction resource with ID = 891234:

```shell
curl -X GET   "https://surveydynamix.com/api/interactions/891234/interaction_data" \
    -u Customer_UUID:Auth_Token
```
Gets a list of interaction data for the requested interaction

This works the same as a GET  call to the /interaction_data resource with the interaction_id parameter set to `{interaction_id}`

### URI
`/interactions/{interaction_id}/responses`
### Method
`GET`

### Parameters
See [Get Interaction Data List.](#get-interaction-data-list)


## Start Survey

> This code will start the survey for interaction with ID = 891234

```shell
curl -X POST   "https://surveydynamix.com/api/interactions/891234/start_survey" \
    -u Customer_UUID:Auth_Token
```
> The request will return a JSON object with the following example structure:

```json
{
  "prompts":[
     "This is the first survey prompt text",
     "This is the second survey prompt text",
     # ...
     "This is the Nth survey prompt text",],
  "sound_files":[
     "http://First_sound_file_url.mp3",
     "http://Second_sound_file_url.mp3",
     # ...
     "http://Nth_sound_file_url.mp3",],
  "survey_completed": 0,
  "current_question":{
    #question resource object for current question if survey_completed = 0
  }
}
```

 Starts a web based survey (if not already started) and returns lists of the current survey prompts and sound files if relevant. Also returns details of current question if a question response is expected.


### URI
`/interactions/{interaction_id}/start_survey`

### Method
`POST`

### Parameters
None

## Submit Survey Response

> This code will submit the response "Yes" to the survey for interaction with ID = 891234

```shell
curl -X POST   "https://surveydynamix.com/api/interactions/891234/submit_response" \
    -d "response=Yes" \
    -u Customer_UUID:Auth_Token
```
> The request will return a JSON object with the following example structure:

```json
{
  "prompts":[
     "This is the first survey prompt text",
     "This is the second survey prompt text",
     # ...
     "This is the Nth survey prompt text",],
  "sound_files":[
     "http://First_sound_file_url.mp3",
     "http://Second_sound_file_url.mp3",
     # ...
     "http://Nth_sound_file_url.mp3",],
  "survey_completed": 0,
  "current_question":{
    #question resource object for current question if survey_completed = 0
  }
}
```

Submits a response to the current survey question, evaluates the response, then returns lists of the current survey prompts and sound files if relevant. Also returns details of current question if a question response is expected. If the interaction has not yet started, this will redirect to the [Start Survey](#start-survey) call instead.


### URI
`/interactions/{interaction_id}/submit_response`

### Method
`POST`

### Parameters
| Name | Description | Allowed Values | Default
| --- | --- | --- | --- |
| response |The string response sent by the survey respondent. | Any string response. | Required |

## Abandon Survey

> This code will finish the survey for interaction with ID = 891234

```shell
curl -X POST   "https://surveydynamix.com/api/interactions/891234/abandon_survey" \
    -u Customer_UUID:Auth_Token
```
> The request will return a JSON object with the following example structure:

```json
{
  "prompts":[
     "This is the first survey prompt text",
     "This is the second survey prompt text",
     # ...
     "This is the Nth survey prompt text",],
  "sound_files":[
     "http://First_sound_file_url.mp3",
     "http://Second_sound_file_url.mp3",
     # ...
     "http://Nth_sound_file_url.mp3",],
  "survey_completed": 1
}
```

Abandons or completes a web based survey and returns lists of the current survey prompts and sound files if relevant.

### URI
`/interactions/{interaction_id}/abandon_survey`

### Method
`POST`

### Parameters
None