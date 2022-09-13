# Mobilefoce WebHook To Forwarding Changes To Customers

## For Any EasyCLM client

We have built the ability for Any EasyCLM app to takes these properties and sent a callback transaction to specified customer's receiver.

|Property| Sample Value|
|---|---|
|external-webhook-tables|List of tables to check and sent changes|
|external-webhook-url|https://apps.mobileforcesoftware.com/customers/axerve/mobileforce/test_callback.php|
|external-webhook-api-key|Vt3lNExI5CGasaBDXhvLvfiLkRTvLeqhrD3QHG5aR89Mctw4mADDsDSTZEZhwdBSBVCtHJ7|
* Param prefix which is usually easyclm- must preced these properties

### Callback Format
For every create or update in specified tables, the callback-url will receive a package with 6 Attributes

|Attribute Name|Description|
|---|---|
|api-key|API Key from property|
|action|'create' or 'update'|
|table|The Table of created or changed data|
|id|ID number of created or updated record|
|data|Array of values of table record after change|
|old_data|Array of values of table record before change.  Field not exist for 'create' action|

### Example
If ServiceTask field Stato Change has value changed 

from Aperto (service_task_status_id = 1)

to Pianificato (service_task_status_id = 2)

Then the callback URL will receive a package of

```text
(
    [api-key] => Vt3lNExI5CGasaBDXhvLvfiLkRTvLeqhrD3QHG5aR89Mctw4mADDsDSTZEZhwdBSBVCtHJ7
    [action] => create
    [table] => ServiceTask
    [id] => 213074
    [data] => Array
        (
            [id] => 213074
            [account_id] =>
...
            [causale1__c] => 1
            [description] => test description
            [service_task_status_id] => 2
        )

    [old_data] => Array
        (
            [id] => 213074
            [name] => Test API1
            [service_task_status_id] => 1
            [service_task_type_id] => 9
...
        )

)

```
