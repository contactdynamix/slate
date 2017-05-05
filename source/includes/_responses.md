# Responses

## Description

> Response resources follow this example format in JSON

```json
{
"id": 124890182,
"interaction_id": 24062,
"question_id": 879,
"response": "Lorem Ipsum dolor sit.",
"submitted_at": "2016-02-19 10:30:02",
"recording_url": "<Twilio Voice Recording URL>",
"response_type": "text",
"question_label": "<Question label for reporting use>"
}
```

A response resource details the response given by a survey respondent to a question during an interaction. The complete results of a survey interaction are represented by a list of survey response objects for each question in the survey.

The response resource API is used to retrieve detailed survey results from Survey Dynamix and can be queried by survey, question, or specific interaction. Each response JSON object contains the following information:

* A string containing response given by the survey respondent

* the type of response it was (text, yesno, nps, or number)

* a unique response ID

* the ID of the interaction it belongs to

* the ID of the question it was in response to

* the timestamp when the response was submitted.

<aside class="notice" > Response resources are read only. </aside>

## Get Responses List

> This code will return a JSON array of the most recent 100 response resources associated with the survey resource with ID = 52:

```shell
curl -X GET   "https://surveydynamix.com/api/responses?survey_id=52&_limit=100&_order=DESC" \
    -u Customer_UUID:Auth_Token
```


Gets a list of survey responses associated with a survey, question, or interaction resource.

At least one of `survey_id`, `question_id`, or `interaction_id` must be specified.

### URI
`/responses`

### Method
`GET`

### Parameters

| Name 	| Description 	| Allowed Values 	| Default 	|
|-------------------	|------------------------------------------------------------------------	|------------------------------	|---------	|
| survey_id 	| The ID of the survey resource the responses is associated with. 	| integer 	| none 	|
| question_id 	| The ID of the question resource the responses is associated with. 	| integer 	| none 	|
| interaction_id 	| The ID of the interaction resource the responses is associated with. 	| integer 	| none 	|
| _limit 	| The number of matching responses to return. 	| integer between 1 and 1000 	| 10 	|
| _offset 	| The row number to start at if more than _limit responses are found. 	| integer 	| 0 	|
| _order 	| The order of ID that results should be returned in. 	| ‘ASC’: earliest first 	| DESC 	|
|  	|  	| or ‘DESC’: most recent first 	|  	|
| response 	| Filters results to only where the response exactly equals this string. 	| string 	| none 	|
| response_contains 	| Filters results to where the response contains this string 	| string 	| none 	|

## Get Specific Response

> This code will return a JSON object for the response resource with ID = 124890182:

```shell
curl -X GET   "https://surveydynamix.com/api/responses/124890182" \
    -u Customer_UUID:Auth_Token
```

Returns the JSON object for a response resource specified by `{response_id}`.

### URI
`/responses/{response_id}`

### Method
`GET`

### Parameters
None