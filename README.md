This README is for developers who would like to...

Please make a copy of xxx and send it to yyy for review and approval.

Method of request

POST
parameters are passed by JSON 

GET
parameters are passed by query string

Both method needs to be SSL supported

Please state carely what are your required parameters.

Below is a list of supported parameters.

Please state which parameters you wish to be passed to your ad server and by what name.



# Requirements

* Provide us an ad request endpoint URL
  - Both POST and GET are supported  

* Your response should be in JSON, which must contain the following information
  - Price (CPM and in USD)
  - HTML snippet for the creative

* Above integration need support SSL/TLS

# Example
## url for requesting ad: 

```
https://bidder.example.com/request?channelid=3345678&cb=86654516519
```
### bid parameters
|Name|Scope|Description|Example|
|---|---|---|---|
|channelid|required|The channel ID from integration partner| 3345678 |
|cb|required|Cache buster|86654516519|


## Optional parameters provide
|Name|Description|Example|
|---|---|---|
|url|url of adslot|'`https://current.scupio.com/`'|
|referrer|referrer of adslot|'`https://previous.scupio.com/`'|
|inif|adslot is in iframe or not|1|


## Response of requesting ad
```
{
    cpm: 0.12189377844333649,
    creative: '<iframe src="https://bidder.example.com/render.html"></iframe>'
}
```

### Response parameters
|Name|Scope|Description|Example|
|---|---|---|---|
|cpm|required|The cpm of return creative, USD| 0.12189377844333649 |
|creative|required|The html snippet which can render ad|'`<iframe src="https://bidder.example.com/render.html"></iframe>`'|

