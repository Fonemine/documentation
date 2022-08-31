# Mobilefoce AXERVE postupdate Hook

## For ServiceTask/(=Ticket)

We have built the ability for Axerve App to take 2 properties

|Property| Sample Value|
|---|---|
|external-callback-url|https://apps.mobileforcesoftware.com/customers/axerve/mobileforce/test_callback.php|
|external-api-key|Vt3lNExI5CGasaBDXhvLvfiLkRTvLeqhrD3QHG5aR89Mctw4mADDsDSTZEZhwdBSBVCtHJ7|

### Callback Format
For every change in ServiceTask, the callback-url will receive a package with 4 Attributes

|Attribute Name|Description|
|---|---|
|api-key|API Key from property|
|service_task_id|ID number for ServiceTask|
|data|Array of values of ServiceTask after change|
|old_data|Array of values of ServiceTask before change|

### Example
If ServiceTask field Stato Change has value changed 

from Aperto (service_task_status_id = 1)

to Pianificato (service_task_status_id = 2)

Then the callback URL will receive a package of

```text
(
    [api-key] => Vt3lNExI5CGasaBDXhvLvfiLkRTvLeqhrD3QHG5aR89Mctw4mADDsDSTZEZhwdBSBVCtHJ7
    [service_task_id] => 213074
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
