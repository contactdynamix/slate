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