# Phone Numbers

## Description

> Phone number lookup results follow this example format in JSON

```json
{
    "phone_number": "+61499999999",
    "country_code": "AU",
    "national_format": "0499 999 999",
    "phone_type": "mobile"
}
```

Phone numbers in SDX are required to be in a specific international format. This resource allows you to lookup a phone number and get basic details including it's correct format for SDX, where it is located, and whether it is able to receive SMS surveys.

Each phone number lookup result contains the following information:

* The phone number in the correct format expected by Survey Dynamix

* The country code of where the phone number is registered

* The national format for the phone number

* The phone type. This is either mobile, landline, or voip.


<aside class="notice"> Mobile numbers are usually able to receive SMS surveys, while voip numbers are uncertain, and landline numbers are usually invalid. If an SMS survey interaction is created for an invalid SMS number, the interaction will not be performed at the scheduled time and will instead be marked as abandoned. </aside>


## Get Phone Number Details

> This code will return the details of the Australian mobile number 0499999999 in the correct format required by Survey Dynamix

```shell
curl -X GET   "https://surveydynamix.com/api/phone_numbers/0499999999?country_code=AU" \
    -u Customer_UUID:Auth_Token
```

Gets a the specific details of a phone number. If the phone number is not valid, a 404 response will be returned instead.

### URI
`/phone_numbers/{phone_number}`

### Method
`GET`

### Parameters

| Name 	| Description 	| Allowed Values 	| Default 	|
|-------------------	|------------------------------------------------------------------------	|------------------------------	|---------	|
| country_code 	| The ISO country code of the phone number.  This is used to specify the country when the number is provided in a national format.	| String  	| US 	|