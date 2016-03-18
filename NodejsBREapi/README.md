# NodejsBREapi
[![Deploy to Azure](http://azuredeploy.net/deploybutton.png)](https://azuredeploy.net/)
 
## Deploying ##
Click the "Deploy to Azure" button above.  You can create new resources or reference existing ones (resource group, gateway, service plan, etc.)  **Site Name and Gateway must be unique URL hostnames.**  The deployment script will deploy the following:
* Resource Group (optional)
* Service Plan (if you don't reference exisiting one)
* Gateway (if you don't reference existing one)
* API App (JavaScriptAPI)
* API App Host (this is the site behind the api app that this github code deploys to)

## API Documentation ##
The API app has one action - Validate - which returns "Result" array parameter. 

## Specification Basics

A NodejsBREapi compliant file is a JSON document that contains an array that is a list of objects for each of your rule definitions.  In the simplest form, a complaint document looks like this:
```json
[
  {
    "rule": {
      "condition": "email_address",
      "property": "user.email"
    }
  }
]
```
Each rule object in the array is defined by the following main properties:

 - id: *optional*
 - description: *optional*
 - rule: **required**
    - property: **required**
    - condition: **required**
 - actions: *optional*

Unless custom actions are defined, the engine should simply evaluate the defined rule as boolean true or false.

### Defining a Rule

#### Valid Conditions

##### Custom function call
 - call
  - function

##### Formatting

 - email_address
 - zipcode
 - yyyy_mm_dd_hh_mm_ss
 - yyyy_mm_dd_hh_mm
 - yyyy_mm_dd
 - mm_dd_yyyy
 - yyyy
 - hh_mm
 - hh_mm_ss
 - matches_regex
  - value

##### Value Comparison

###### Numeric

 - is_integer
 - is_float
 - equal
  - value
 - equal_property
  - value
 - not_equal
  - value
 - not_equal_property
  - value
 - greater_than
  - value
 - greater_than_property
  - value
 - less_than
  - value
 - less_than_property
  - value
 - greater_than_or_equal
  - value
 - greater_than_or_equal_property
  - value
 - less_than_or_equal
  - value
 - less_than_or_equal_property
  - value
 - between
  - start
  - end

###### String

 - equal
  - value
 - equal_property
  - value
 - not_equal
  - value
 - not_equal_property
  - value
 - starts_with
  - value
 - ends_with
  - value
 - contains
  - value
 - not_empty
 - is_empty

###### Boolean

 - is_true
 - is_false

###### List

 - in
  - values
 - not_in
  - values
 - contains
  - value
 - does_not_contain
  - value
 - includes_all
  - values
 - includes_none
  - values

#### Combining Conditions

 - if
 - then
 - and
 - or

### Defining Actions

 - callOnTrue
  - args
 - callOnFalse
  - args
 - returnOnTrue
 - returnOnFalse

## Examples
- [simple_example.json](../../raw/master/examples/simple_example.json)
 - [advanced_example.json](../../raw/master/examples/advanced_example.json)
 

