# MobileForce API Documentation

## Introduction

The MobileForce API allows one to view and modify tables used in the MobileForce platform.
Example tables are are ServiceTasks, Accounts, Contacts, and so on.  One can create, read,
update, and delete individual objects in the table, as well as fetch multiple objects in a table.

## Calling the API

### API Key

To use the MobileForce API, you need an API key.  This key is specific to your account
and will be provided to you by MobileForce support.  This key may be different
when using the stage and production versions of the MobileForce platform.

### API Endpoints

All MobileForce API calls are done via a HTTPS POST to a single API endpoint.
The endpoint API can vary based on your geographic region and whether you are using
using the production or staging version of MobileForce platform.

The supported endpoints are:

|Instance | API endpoint |
|---|---|
|Production | `https://apps.mobileforcesoftware.com/adlwebui/service/mf_api.php` |
|Stage | `https://apps.mobileforcesoftware.com/stage/adlwebui/service/mf_api.php` |

### Required HTTP Headers

The API endpoint requires these HTTP headers:

* `Content-Type`: The content encoding type.  Should be `application/x-www-form-urlencoded` or `multipart/form-data`.
* `api_key`: API key provided by MobileForce support.

### HTTP POST Parameters

The API endpoint must be invoked via a
[HTTP POST](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/POST)
using one of the standard form encoding types.
The following encoding types are supported:

* `application/x-www-form-urlencoded`
* `multipart/form-data`

Use `multipart/form-data` if you need to upload a file.  Otherwise, use `application/x-www-form-urlencoded`.

The following POST parameters are required for all API actions:

* `table`: The name of the MobileForce table to read or update.
* `action`: Type of action to perform on this MobileForce table.  Must be: `create`, `read`, `update`, `delete`, or `list`.

Additional POST parameters may be required or accepted based on the action type.

### Passing in object fields

The `create` and `update` actions require passing object fields to the server.
This is done by passing in POST parameters whose names are of the form `d_<field-name>`,
where `<field-name>` is the name of the field.
For example, to update the `name` field of an object, you must set the POST
parameter `d_name`.

## API Responses

All API responses will be JSON objects.  This JSON object will have the following fields:

* `status`: The status of the response.  May be `success` or `failure`.
* `message`: The status message.  If the action failed, this will contain the failure message.

### Error Message info

Here are some common error messages and how to handle them.

|Error|Description|
|-----|----------|
|Version `<v2>` not supported|Check `api_key` header value|
|Invalid datatable response|Internal error. Please contact MF Support|
|Action `<action>` not supported| Check the POST param `action`. Only `create` and `update` actions are supported.|
|Invalid api_key| Check the header API key|
|Object `<object>` access denied| Object is not exposed to external world. Please contact MF Support. |
|Missing api_key header| Cheek the POST http header.|
|Missing account or app parameter| Problem with api_key. Please contact MF support|

## API Actions

This section describes each of the API actions in more detail.

### List Action

The `list` action is used to read one more objects in a table.

Only a subset of all the fields of an object is fetched.  If you need to fetch a field
not in this subset, include it in the `additionalcolumns` parameter.

#### Request

* `table`: *(required)* The name of the MobileForce table to read or update.
* `action`: *(required)* Must be `list`.
* `search`: Expression to search by.  This expression uses SQL WHERE condition syntax.  Example search expressions are `owner_id = 123` or `name LIKE '%john%' AND is_lead = 1`.
* `additionalcolumns`: Comma-separated list of additional columns to read.
* `offset`: Offset of first object to fetch.  If not specified, it defaults to 0, the first object in the results.)
* `length`: Number of objects to fetch.  If not specified, only at most 10 objects are fetched.

#### Response

The response is a JSON object with the following parameters:

* `status`: The status of the response.  May be `success` or `failure`.
* `message`: The status message.  If the action failed, this will contain the failure message.
* `items`: Array of objects that were fetched.

Each object in the list of objects will have the following fields:

* `id`: ID of the object
* `label`: Displayed name of the object.  Usually the `name` field in the object.
* `icon`: *(deprecated)* No longer used.
* `link`: Mobileforce UI link for object.  Will not work outside of a MobileForce UI.  Do not use.
* `info`: Array of fields and their values for the object.  Each element will have the following fields:
  * `name`: Field name
  * `label`: Displayed label for the field.
  * `value`: Field value
  * `valueType`: Field's type.
  * `numLines`: *(deprecated)*  No longer used.

#### Example

##### Request

```text
POST https://apps.mobileforcesoftware.com/adlwebui/service/mf_api.php HTTP/1.1
Content-Type: application/x-www-form-urlencoded
api_key: $mf3$AwGOfDJYhfFjN3RVlF+rlR1dCe7f3JvmqZwv3

POST DATA
------------------------------------
action=list
object=ServiceTask
offset=0
length=10
search=name like '%test%'
```

##### Response

```text
Content-Type: application/json

{
  "status": "success",
  "message": "",
  "rowcount": "5",
  "items": [
    {
      "label": "Test API111",
      "id": "213119",
      "icon": "",
      "link": "datatableformscreen.php?path=Home%3Beasyclm-ServiceTask&action=read&table=ServiceTask&s=eJxLrEgtKkutyc1PysxJTcsvSk6tMQQCAzMTMxMLo5pI1-CamhqDGkM9Az0DEKPGK6_Y19DJ0SUivDIDAJ8BFNc&layouttype=&id=213119",
      "info": [
        {
          "name": "name",
          "label": "Nome",
          "value": "Test API111",
          "valueType": "text",
          "numLines": 1
        },
        {
          "name": "service_task_status_id",
          "label": "Stato",
          "value": "Chiuso",
          "valueType": "text",
          "numLines": 1
        },

    ....
    ....
    }
   ]
}
```

### Read Action

The `read` action reads the object with the given ID in the given table.

#### Request

* `table`: *(required)* The name of the MobileForce table to read or update.
* `action`: *(required)* Must be `read`.
* `id`: *(required)* The ID of the object to read.

#### Response

The response is a JSON object with the following parameters:

* `status`: The status of the response.  May be `success` or `failure`.
* `message`: The status message.  If the action failed, this will contain the failure message.
* `id`: ID of the object
* `items`: Array of fields and their values for the object.  Each element will have the following fields:
  * `name`: Field name
  * `label`: Displayed label for the field.
  * `value`: Field value

#### Example

##### Request

```text
POST https://apps.mobileforcesoftware.com/adlwebui/service/mf_api.php HTTP/1.1
Content-Type: application/x-www-form-urlencoded
api_key: $mf3$AwGOfDJYhfFjN3RVlF+rlR1dCe7f3JvmqZwv3

POST DATA
------------------------------------
action=read
object=ServiceTask
id=213074
```

##### Response

```text
Content-Type: application/json

{
  "status": "success",
  "message": "Record deleted successfully",
  "id": 213074,
  "items" : [
    {"name":"name","label":"Name","value":"Test API11 update3"},
    {"name":"service_task_status_id","label":"Service Task Status","value":"4"},
    .....
    .....
   ]
}
```

### Create Action

#### Request

The `create` action accepts the following POST parameters:

* `table`: *(required)* The name of the MobileForce table to read or update.
* `action`: *(required)* Must be `create`.
* `d_<field-name>`: Value of the field to update in object.  One can specify multiple
  fields by providing a `d_<field-name>` parameter for each field

#### Response

The response is a JSON object with the following parameters:

* `status`: The status of the response.  May be `success` or `failure`.
* `message`: The status message.  If the action failed, this will contain the failure message.
* `id`: ID of the newly created object

#### Example

##### Request

```text
POST https://apps.mobileforcesoftware.com/adlwebui/service/mf_api.php HTTP/1.1
Content-Type: application/x-www-form-urlencoded
api_key: $mf3$AwGOfDJYhfFjN3RVlF+rlR1dCe7f3JvmqZwv3

POST DATA
-----------------------------------
action=create
object=ServiceTask
d_name=Name
d_service_task_status_id=1
d_service_task_type_id=9
d_causale_c__c=CAUSALE DI CHIUSURA TICKET DA REINSTALLAZIONE
d_argomento__c=Abilitare alle carte di credito
d_work_order_id=<work_order_id>
d_termid_id__c=<Termid ID>
d_sugarcrm_account__c={"key":"140177","value":"TOT PER LA MUSICA"}
d_description=test description
d_note_apertura__c=
d_closing_notes=
d_data_scadenza__c=<yyyy-mm-dd>
d_office_id=13
d_street_address=924 Borregas Ave
d_city - Optional=Son Jose
d_state_or_province=CA
d_zip_or_postal_code=95059
d_country=United States of America
d_phone=3334445555
d_email=test@test.com
d_office_id=
d_service_estimated_hours=1
d_service_estimated_days=1
d_billable=1
d_service_amount_due=100
d_payment_date=
d_payment_type=
d_alfaticket__c=
d_data_ape__c=2022-01-01
d_ttdatult__c=2022-01-01
d_data_pianificazione__c=2022-01-01
d_reinvio_pianificazione__c=
d_note_task_piani__c=
```

##### Response

```text
Content-Type: application/json

{
  "status": "success",
  "message": "",
  "id": 213074
}
```

### Update Action

The `update` action updates one or more fields in the object with the given ID
in the given table.

#### Request

* `table`: *(required)* The name of the MobileForce table to read or update.
* `action`: *(required)* Must be `update`.
* `id`: *(required)* The ID of the object to update.
* `d_<field-name>`: Value of the field to update in object.  One can specify multiple
  fields by providing a `d_<field-name>` parameter for each field

#### Response

The response is a JSON object with the following parameters:

* `status`: The status of the response.  May be `success` or `failure`.
* `message`: The status message.  If the action failed, this will contain the failure message.
* `id`: ID of the object
* `items`: Array of fields and their values for the object.  Each element will have the following fields:
  * `name`: Field name
  * `label`: Displayed label for the field.
  * `value`: Field value

#### Example

##### Request

```text
POST https://apps.mobileforcesoftware.com/adlwebui/service/mf_api.php HTTP/1.1
Content-Type: application/x-www-form-urlencoded
api_key: $mf3$AwGOfDJYhfFjN3RVlF+rlR1dCe7f3JvmqZwv3

POST DATA
------------------------------------
action=update
object=ServiceTask
id=213074
d_name=Name
d_service_task_status_id=1
d_service_task_type_id=9
d_causale_c__c=CAUSALE DI CHIUSURA TICKET DA REINSTALLAZIONE
d_argomento__c=Abilitare alle carte di credito
d_work_order_id=<work_order_id>
d_termid_id__c=<Termid ID>
d_sugarcrm_account__c={"key":"140177","value":"TOT PER LA MUSICA"}
d_description=test description
d_note_apertura__c=
d_closing_notes=
d_data_scadenza__c=<yyyy-mm-dd>
d_office_id=13
d_street_address=924 Borregas Ave
d_city - Optional=Son Jose
d_state_or_province=CA
d_zip_or_postal_code=95059
d_country=United States of America
d_phone=3334445555
d_email=test@test.com
d_office_id=
d_service_estimated_hours=1
d_service_estimated_days=1
d_billable=1
d_service_amount_due=100
d_payment_date=
d_payment_type=
d_alfaticket__c=
d_data_ape__c=2022-01-01
d_ttdatult__c=2022-01-01
d_data_pianificazione__c=2022-01-01
d_reinvio_pianificazione__c=
d_note_task_piani__c=
```

##### Response

```text
Content-Type: application/json

{
  "status": "success",
  "message": "",
  "id": 213074,
  "items" : [
    {"name":"name","label":"Name","value":"Test API11 update3"},
    {"name":"service_task_status_id","label":"Service Task Status","value":"4"},
    .....
    .....
   ]
}
```

### Delete Action

The `delete` action deleted the object with the given ID in the given table.

#### Request

* `table`: *(required)* The name of the MobileForce table to read or update.
* `action`: *(required)* Must be `delete`.
* `id`: *(required)* The ID of the object to delete.

#### Response

The response is a JSON object with the following parameters:

* `status`: The status of the response.  May be `success` or `failure`.
* `message`: The status message.  If the action failed, this will contain the failure message.
* `id`: ID of the deleted object.

#### Example

##### Request

```text
POST https://apps.mobileforcesoftware.com/adlwebui/service/mf_api.php HTTP/1.1
Content-Type: application/x-www-form-urlencoded
api_key: $mf3$AwGOfDJYhfFjN3RVlF+rlR1dCe7f3JvmqZwv3

POST DATA
------------------------------------
action=delete
object=ServiceTask
id=213074
```

##### Response

```text
Content-Type: application/json

{
  "status": "success",
  "message": "Record deleted successfully",
  "id": 213074,
  "items" : []
}
```

### CURL examples

This section provides some examples on how to invoke the MobileForce API
via linux's [curl](https://linux.die.net/man/1/curl) command.

#### Create action

```sh
curl -X POST \
-H 'api_key: $mf3$AwEfE5I0gCL7YalrOoqZrVc1Swwo038n+me2Vt3lNExI5CGBDXhvLvfiLkRTvLeq3QHG5aR89Mctw4mAsDSTZEZhwdBSBVCtHJ7+ao/OfnIPfGXLGKFKrx92gzeYErCGbMPP/bj083/+39cFyDL4ghkNwetJt0WoNnxKQsv0cbtA8w==' \
-F 'action=create' \
-F 'object=ServiceTask' \
-F 'd_name=Test API111' \
-F 'd_service_task_status_id=4' \
-F 'd_service_task_type_id=9' \
-F 'd_email=test@test.com' \
-F 'd_description=test description' \
-F 'd_office_id=13' \
-F 'd_sugarcrm_account__c={"key":"140177","value":"TOT PER LA MUSICA"}' \
-F 'd_skill_ids=1,2' \
-F 'd_data_ape__c=2022-01-01 21:59:59' \
-F 'd_ttdatult__c=2022-01-01' \
https://apps.mobileforcesoftware.com/adlwebui/service/mf_api.php
```

#### Update action

```sh
curl -X POST \
-H 'api_key: $mf3$AwEfE5I0gCL7YalrOoqZrVc1Swwo038n+me2Vt3lNExI5CGBDXhvLvfiLkRTvLeq3QHG5aR89Mctw4mAsDSTZEZhwdBSBVCtHJ7+ao/OfnIPfGXLGKFKrx92gzeYErCGbMPP/bj083/+39cFyDL4ghkNwetJt0WoNnxKQsv0cbtA8w==' \
-F 'action=update' \
-F 'object=ServiceTask' \
-F 'id=213112' \
-F 'd_name=Test API11 update3' \
-F 'd_service_task_status_id=4' \
-F 'd_service_task_type_id=9' \
-F 'd_email=test@test.com' \
-F 'd_description=test description' \
-F 'd_office_id=13' \
-F 'd_sugarcrm_account__c={"key":"140177","value":"TOT PER LA MUSICA"}' \
-F 'd_skill_ids=1,2' \
-F 'd_data_ape__c=2022-01-01 21:59:59' \
-F 'd_ttdatult__c=2022-01-01' \
https://apps.mobileforcesoftware.com/adlwebui/service/mf_api.php
```

#### Read action

```sh
curl -X POST \
-H 'api_key: $mf3$AwEfE5I0gCL7YalrOoqZrVc1Swwo038n+me2Vt3lNExI5CGBDXhvLvfiLkRTvLeq3QHG5aR89Mctw4mAsDSTZEZhwdBSBVCtHJ7+ao/OfnIPfGXLGKFKrx92gzeYErCGbMPP/bj083/+39cFyDL4ghkNwetJt0WoNnxKQsv0cbtA8w==' \
-F 'action=read' \
-F 'object=ServiceTask' \
-F 'id=213112' \
https://apps.mobileforcesoftware.com/adlwebui/service/mf_api.php
```

#### Delete action

```sh
curl -X POST \
-H 'api_key: $mf3$AwEfE5I0gCL7YalrOoqZrVc1Swwo038n+me2Vt3lNExI5CGBDXhvLvfiLkRTvLeq3QHG5aR89Mctw4mAsDSTZEZhwdBSBVCtHJ7+ao/OfnIPfGXLGKFKrx92gzeYErCGbMPP/bj083/+39cFyDL4ghkNwetJt0WoNnxKQsv0cbtA8w==' \
-F 'action=delete' \
-F 'object=ServiceTask' \
-F 'id=213112' \
https://apps.mobileforcesoftware.com/adlwebui/service/mf_api.php
```

#### List action (All)

```sh
curl -X POST \
-H 'api_key: $mf3$AwEfE5I0gCL7YalrOoqZrVc1Swwo038n+me2Vt3lNExI5CGBDXhvLvfiLkRTvLeq3QHG5aR89Mctw4mAsDSTZEZhwdBSBVCtHJ7+ao/OfnIPfGXLGKFKrx92gzeYErCGbMPP/bj083/+39cFyDL4ghkNwetJt0WoNnxKQsv0cbtA8w==' \
-F 'action=list' \
-F 'object=ServiceTask' \
-F 'offset=0' \
-F 'length=1' \
https://apps.mobileforcesoftware.com/adlwebui/service/mf_api.php
```

#### List action with search

You need to specify "search" post parameter.

```sh
curl -X POST \
-H 'api_key: $mf3$AwEfE5I0gCL7YalrOoqZrVc1Swwo038n+me2Vt3lNExI5CGBDXhvLvfiLkRTvLeq3QHG5aR89Mctw4mAsDSTZEZhwdBSBVCtHJ7+ao/OfnIPfGXLGKFKrx92gzeYErCGbMPP/bj083/+39cFyDL4ghkNwetJt0WoNnxKQsv0cbtA8w==' \
-F 'action=list' \
-F 'object=ServiceTask' \
-F "search=id='213119'" \
-F 'offset=0' \
-F 'length=1' \
https://apps.mobileforcesoftware.com/adlwebui/service/mf_api.php
```

## MobileForce Tables

This section provides more information about the fields for selected MobileForce tables

### ServiceTask

The ServiceTask table contains data for a single schedulable task.

* `d_name`: *(required)* Must be unique
* `d_service_task_type_id` *(required)* Expected values : 1 - Aperto, 2 - Pianificato, 3 - In consegna, 4 - Chiuso, 5 - Annullato, 9 - Chiuso da eliminare, 10 - Chiuso KO, 11 - Consegnato
* `d_service_task_type_id` *(required)* Expected values : 9 - Installazione, 10 - Manutenzione ordinaria, 11 - Manutenzione straordinaria, 12 - Ritiro terminali, 13 - Argentea, 14 - Flex, 15 - Autoconfigurazione
* `d_causale_c__c`: CAUSALE DI CHIUSURA TICKET DA REINSTALLAZIONE, MANUTENZIONE ORDINARIA|MANUTENZIONE ORDINARIA etc.
* `d_argomento__c` - Abilitare alle carte di credito,Aggiornamento Chiavi CB2 etc.
* `d_work_order_id` - Work order ID
* `d_termid_id__c` - Teamid ID
* `d_sugarcrm_account__c` - JSON dictionary string with key and value. For eg. {"key":"140177","value":"TOT PER LA MUSICA"}
* `d_description` - Optional field. Max 1000 characters
* `d_note_apertura__c` - Optional field. Max 255 characters
* `d_closing_notes` - Optional field. Max 1000 characters
* `d_data_scadenza__c` - date ISO 8601 format
* `d_street_address` - Optional field. Max 255 characters
* `d_city` - Optional - Max 255 characters
* `d_state_or_province` - State
* `d_zip_or_postal_code` - Postal Code
* `d_country` - United States of America. Expected values: ´United States of America, Australia...etc
* `d_phone` - Phone number
* `d_email` - Email
* `d_office_id` - Office Id
* `d_service_estimated_hours` - Hours
* `d_service_estimated_days` - Days
* `d_billable` - 0/1
* `d_service_amount_due` - Amount due
* `d_payment_date` -  `<yyyy-mm-dd>`
* `d_payment_type` - Free form text. Max 100 characters.
* `d_alfaticket__c` - Free form text. Max 255 characters
* `d_data_ape__c` - `<yyyy-mm-dd>`
* `d_ttdatult__c` -  `<yyyy-mm-dd>`
* `d_data_pianificazione__c` -  `<yyyy-mm-dd>`
* `d_reinvio_pianificazione__c` - Number format
* `d_note_task_piani__c` - Free form text. Max 255 characters
