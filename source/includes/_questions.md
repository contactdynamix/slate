# Questions

## Description

> Question resources follow this example format in JSON

```json
{
    "id": 509,
    "survey_id": 71,
    "order": 2,
    "question_text": "On a scale from 0 to 10, how likely are you to recommend Survey Dynamix to your family or friends?",
    "max_response": 10,
    "question_type": "nps",
    "question_label": "Basic NPS",
    "question_sound_file": "<sound file url>.mp3"
  }

```

A question resource details the core properties of a question to be asked in an SDX survey.

The question query API can be used to get detailed information about a questions for third party reporting or API response submission

Each question resource contains the following information:

* The question ID

* If queried for a particular survey, the survey id and question order within the survey.

* The question text

* The url of the question sound file

* The question type

* The question max response

* The question label for reporting


<aside class="notice"> Question resources are read only. </aside>

## Get Questions List

> This code will return a JSON array of all question resources part of the survey with id = 52 :

```shell
curl -X GET   "https://surveydynamix.com/api/questions?survey_id=52" \
    -u Customer_UUID:Auth_Token
```

Gets a list of question resources associated with the authenticated customer.

Can be queried by survey id, question type, or question label.

### URI
`/questions`

### Method
`GET`

### Parameters

| Name 	| Description 	| Allowed Values 	| Default 	|
|-------------------	|------------------------------------------------------------------------	|------------------------------	|---------	|
| _limit 	| The number of matching results to return. 	| integer between 1 and 1000 	| 10 	|
| _offset 	| The row number to start at if more than _limit results are found. 	| integer 	| 0 	|
| _order 	| The order of ID that results should be returned in. 	| ‘ASC’: earliest first 	| DESC 	|
|  	|  	| or ‘DESC’: most recent first 	|  	|
| survey_id 	| The ID of the survey resource question is associated with. 	| integer 	| none 	|
| question_type 	| The type of question. 	| number, yesno, text, nps 	| none 	|
| question_label 	| The reporting label of the question. 	| string up to 30 characters long 	| none 	|



## Get Specific Question

> This code will return a JSON object for the question resource with ID = 509:

```shell
curl -X GET   "https://surveydynamix.com/api/questions/509" \
    -u Customer_UUID:Auth_Token
```

Returns the JSON object for a question resource specified by `{question_id}`.

### URI
`/questions/{question_id}`

### Method
`GET`

### Parameters
None


## Get Responses List By Question

> This code will return a JSON array of responses associated with the question resource with ID = 509:

```shell
curl -X GET   "https://surveydynamix.com/api/questions/509/responses" \
    -u Customer_UUID:Auth_Token
```

Gets a list of responses to the requested question.

This works the same as a GET call to the /responses resource with the `question_id` parameter set to `{question_id}`

### URI
`/questions/{question_id}/responses`

###
GET

### Parameters
See [Get Responses List](#get-responses-list)