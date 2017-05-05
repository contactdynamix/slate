# Surveys

## Description

> Survey resources follow this example format in JSON

```json
{
  "id": 52,
  "name": "Test survey",
  "description": "Test survey for development",
  "greeting_text": "Thanks for taking the time to respond to our survey!",
  "instructions_text": "We'd love to get some feedback on your recent customer experience!",
  "closing_text": "Thank you for participating. Goodbye.",
  "email_subject": "Test email survey",
  "email_from_address": "test@surveydynamix.com",
  "email_from_name": "Survey Dynamix API",
  "greeting_sound_file": "<sound file url>.mp3",
  "instructions_sound_file": "<sound file url>.mp3",
  "closing_sound_file": "<sound file url>.mp3",
  "inbound_number": "+61999999999",
  "outbound_number": "+61999999999",
  "sms_number": "+61888888888"
}
```

A survey resource details the core properties of a survey within SDX.

The survey query API can be used to get detailed information about a survey for third party reporting or API response submission

Each survey resource contains the following information:

* The survey ID

* The survey name

* A description of the survey

* The greeting, instructions, and closing prompts

* The greeting, instructions, and closing sound file URLs

* Email subject prompt

* Email from details

* Voice connection numbers for inbound, outbound, and sms

<aside class="notice"> Survey resources are read only. </aside>

## Get Surveys List

> This code will return a JSON array of all survey resources associated with the authenticated customer:

```shell
curl -X GET   "https://surveydynamix.com/api/surveys?_limit=1000" \
    -u Customer_UUID:Auth_Token
```

Gets a list of survey resources associated with the authenticated customer.

### URI
`/surveys`

### Method
`GET`

### Parameters

| Name 	| Description 	| Allowed Values 	| Default 	|
|-------------------	|------------------------------------------------------------------------	|------------------------------	|---------	|
| _limit 	| The number of matching results to return. 	| integer between 1 and 1000 	| 10 	|
| _offset 	| The row number to start at if more than _limit results are found. 	| integer 	| 0 	|
| _order 	| The order of ID that results should be returned in. 	| ‘ASC’: earliest first 	| DESC 	|
|  	|  	| or ‘DESC’: most recent first 	|  	|



## Get Specific Survey

> This code will return a JSON object for the survey resource with ID = 52:

```shell
curl -X GET   "https://surveydynamix.com/api/surveys/52" \
    -u Customer_UUID:Auth_Token
```

Returns the JSON object for a survey resource specified by `{survey_id}`.

### URI
`/surveys/{survey_id}`

### Method
`GET`

### Parameters
None


## Get Questions List By Survey


> This code will return a JSON array of question resources that are part of the survey resource with ID = 52:

```shell
curl -X GET   "https://surveydynamix.com/api/surveys/52/questions" \
    -u Customer_UUID:Auth_Token
```

Gets a list of questions that are part of the requested survey.

This works the same as a GET call to the /questions resource with the `survey_id` parameter set to `{survey_id}`

### URI
`/surveys/{survey_id}/questions`

###
GET

### Parameters
See [Get Questions List](#get-questions-list)


## Get Interactions List By Survey


> This code will return a JSON array of interaction resources that are associated with the survey resource with ID = 52:

```shell
curl -X GET   "https://surveydynamix.com/api/surveys/52/interactions" \
    -u Customer_UUID:Auth_Token
```

Gets a list of interactions that are associated with the requested survey.

This works the same as a GET call to the /interactions resource with the `survey_id` parameter set to `{survey_id}`

### URI
`/surveys/{survey_id}/interactions`

###
GET

### Parameters
See [Get Interactions List](#get-interactions-list)


## Get Interaction Data List By Survey

> This code will return a JSON array of interaction data resources that are associated with the survey resource with ID = 52:

```shell
curl -X GET   "https://surveydynamix.com/api/surveys/52/interaction_data" \
    -u Customer_UUID:Auth_Token
```

Gets a list of interaction data resources that associated with of the requested survey.

This works the same as a GET call to the /interaction_data resource with the `survey_id` parameter set to `{survey_id}`

### URI
`/surveys/{survey_id}/interaction_data`

###
GET

### Parameters
See [Get Interaction Data List](#get-interaction-data-list)


## Get Responses List By Survey

> This code will return a JSON array of response resources that are associated with the survey resource with ID = 52:

```shell
curl -X GET   "https://surveydynamix.com/api/surveys/52/responses" \
    -u Customer_UUID:Auth_Token
```

Gets a list of responses that are associated with the requested survey.

This works the same as a GET call to the /responses resource with the `survey_id` parameter set to `{survey_id}`

### URI
`/surveys/{survey_id}/responses`

###
GET

### Parameters
See [Get Responses List](#get-responses-list)