# MobileForce API Documentation

MobileForce API can be used be other application to create/update MobileForce specific objects like ServiceTasks, Accounts, Contacts etc. API is authenticated thru API key which is generated onetime by MobileForce administrator. External application should make sure API key is securely stored and all network connection should use "https" protocol.

## URI

|Instance | API endpoint |
|---|---|
|Production | https://apps.mobileforcesoftware.com/adlwebui/service/mf_api.php|
|Stage | https://apps.mobileforcesoftware.com/stage/adlwebui/service/mf_api.php|

## HTTP Header:
    api_key: <api-key provide by MobileForce Support>

Note: dev/stage/production environment might have different API key.

## HTTP Method
    POST - You should use POST HTTP method for all the API calls using form-data method(key value pair for each field). If files need to updated, you need to post data as multipart form-data(application/x-www-form-urlencoded).


## HTTP POST params

    * table - This specifies the object name that need to be created. For e.g. ServiceTask, Account etc.
    * action - This specifies the action that needs to be preformed on the object. Following are the action that are currently supported - create and update
    * d_<field-name> - All the fields starting with prefix "d_" should be present in object property spec.



# RESPONSE

Response will be HTTP 200 with JSON string.

## Success response

```json
{
    "status" : "success",
    "message" : "Update success",
    "id" : "id"
}
```
On create/update action, the response will always have "id" field which corresponds to the newly created or updated object.

## Failure response

```json
{
    "status" : "failure",
    "message" : "Invalid api_key"
}
```

## Error Message info

|Error|Description|
|-----|----------|
|Version `<v2>` not supported|Check mf_api key header value|
|Invalid datatable response|Internal error. Please contact MF Support|
|Action `<action>` not supported| Check the POST param "action". Only "create" and "update" actions are supported.|
|Invalid api_key| Check the header API key|
|Object <object> access denied| Object is not exposed to external world. Please contact MF Support. |
|Missing api_key header| Cheek the POST http header.|
|Missing account or app parameter| Problem with api_key. Please contact MF support|



## Example ServiceTask object

### Create action

"d_name" should be unique value, otherwise API will return error response.

```text
POST https://apps01.mobileforcesoftware.com/prabu/adlwebui/service/mf_api.php HTTP/1.1
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

Response
----------

```text
Content-Type: application/json

{
  "status": "success",
  "message": "",
  "id": 213074
}
```

### Update action

For update action "id" must be specified. Object with "id" will be updated accordingly.


```text
POST https://apps01.mobileforcesoftware.com/prabu/adlwebui/service/mf_api.php HTTP/1.1
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

Response
----------

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

### Field details

* d_name - Required  and it should be unique
* d_service_task_type_id - Required. Expected values : 1 - Aperto, 2 - Pianificato, 3 - In consegna, 4 - Chiuso, 5 - Annullato, 9 - Chiuso da eliminare, 10 - Chiuso KO, 11 - Consegnato
* d_service_task_type_id - Required. Expected values : 9 - Installazione, 10 - Manutenzione ordinaria, 11 - Manutenzione straordinaria, 12 - Ritiro terminali, 13 - Argentea, 14 - Flex, 15 - Autoconfigurazione
* d_causale_c__c - CAUSALE DI CHIUSURA TICKET DA REINSTALLAZIONE, MANUTENZIONE ORDINARIA|MANUTENZIONE ORDINARIA etc.
* d_argomento__c - Abilitare alle carte di credito,Aggiornamento Chiavi CB2 etc.
* d_work_order_id - Work order ID
* d_termid_id__c - Teamid ID
* d_sugarcrm_account__c - JSON dictionary string with key and value. For eg. {"key":"140177","value":"TOT PER LA MUSICA"}
* d_description - Optional field. Max 1000 characters
* d_note_apertura__c - Optional field. Max 255 characters
* d_closing_notes - Optional field. Max 1000 characters
* d_data_scadenza__c - date ISO 8601 format
* d_street_address - - Optional field. Max 255 characters
* d_city - Optional - Max 255 characters
* d_state_or_province - State
* d_zip_or_postal_code - Postal Code
* d_country - United States of America. Expected values: ´United States of America, Australia...etc
* d_phone - Phone number
* d_email - Email
* d_office_id - Office Id
* d_service_estimated_hours - Hours
* d_service_estimated_days - Days
* d_billable - 0/1
* d_service_amount_due - Amount due
* d_payment_date -  `<yyyy-mm-dd>`
* d_payment_type - Free form text. Max 100 characters.
* d_alfaticket__c - Free form text. Max 255 characters
* d_data_ape__c - `<yyyy-mm-dd>`
* d_ttdatult__c -  `<yyyy-mm-dd>`
* d_data_pianificazione__c -  `<yyyy-mm-dd>`
* d_reinvio_pianificazione__c - Number format
* d_note_task_piani__c - Free form text. Max 255 characters
    
    
### Delete action

For delete action "id" must be specified. Object with "id" will be deleted accordingly.


```text
POST https://apps01.mobileforcesoftware.com/prabu/adlwebui/service/mf_api.php HTTP/1.1
Content-Type: application/x-www-form-urlencoded
api_key: $mf3$AwGOfDJYhfFjN3RVlF+rlR1dCe7f3JvmqZwv3

POST DATA
------------------------------------
action=delete
object=ServiceTask
id=213074
```

Response
----------

```text
Content-Type: application/json

{
  "status": "success",
  "message": "Record deleted successfully",
  "id": 213074,
  "items" : []
}
```
    
### Search/list action

Default value for "length" is 10. You sepecify SQL like search string. 

```text
POST https://apps01.mobileforcesoftware.com/prabu/adlwebui/service/mf_api.php HTTP/1.1
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

Response
----------

```text
Content-Type: application/json

{
  "status": "success",
  "message": "",
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
    
    
### Curl examples
    
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
https://apps01.mobileforcesoftware.com/prabu/adlwebui/service/mf_api.php
```
#### Update action
    
```sh
curl -X POST \
-H 'api_key: $mf3$AwEfE5I0gCL7YalrOoqZrVc1Swwo038n+me2Vt3lNExI5CGBDXhvLvfiLkRTvLeq3QHG5aR89Mctw4mAsDSTZEZhwdBSBVCtHJ7+ao/OfnIPfGXLGKFKrx92gzeYErCGbMPP/bj083/+39cFyDL4ghkNwetJt0WoNnxKQsv0cbtA8w==' \
-F 'action=create' \
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
https://apps01.mobileforcesoftware.com/prabu/adlwebui/service/mf_api.php
```  
    
#### Delete action
    
```sh
curl -X POST \
-H 'api_key: $mf3$AwEfE5I0gCL7YalrOoqZrVc1Swwo038n+me2Vt3lNExI5CGBDXhvLvfiLkRTvLeq3QHG5aR89Mctw4mAsDSTZEZhwdBSBVCtHJ7+ao/OfnIPfGXLGKFKrx92gzeYErCGbMPP/bj083/+39cFyDL4ghkNwetJt0WoNnxKQsv0cbtA8w==' \
-F 'action=delete' \
-F 'object=ServiceTask' \
-F 'id=213112' \
https://apps01.mobileforcesoftware.com/prabu/adlwebui/service/mf_api.php
```   

#### List/Search action
    
```sh
curl -X POST \
-H 'api_key: $mf3$AwEfE5I0gCL7YalrOoqZrVc1Swwo038n+me2Vt3lNExI5CGBDXhvLvfiLkRTvLeq3QHG5aR89Mctw4mAsDSTZEZhwdBSBVCtHJ7+ao/OfnIPfGXLGKFKrx92gzeYErCGbMPP/bj083/+39cFyDL4ghkNwetJt0WoNnxKQsv0cbtA8w==' \
-F 'action=list' \
-F 'object=ServiceTask' \
-F "search=id='213119'" \
-F 'offset=0' \
-F 'length=1' \
https://apps01.mobileforcesoftware.com/prabu/adlwebui/service/mf_api.php
```   
