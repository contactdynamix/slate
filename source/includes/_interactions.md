# Interactions
## Description
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

## JSON Representation
Interaction resources follow this example format


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

## Get Interactions List
Gets a list of survey interactions
### URI
`/interactions`
### Method
`GET`

### Parameters
| Name | Description | Allowed Values | Default
| --- | --- | --- | --- |