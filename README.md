# [Insert name of the project]

This README is for developers who wish to make a request to integrate their frontend ad bidders with [CONFIRM NAME].

Following are steps for guiding you to making the integration. 
1. Decide your bid request endpoint url, and request method
2. Implement the bid response
3. Copy and fill the technical form from [SOME TO BE ADDED URL] and send it to [SOME EMAIL, PROBABILY MARKETING PEOPLE].

# Requirements

* Bid-request endpoints must support HTTPS 
* Bid-response must be AJAX with JSON responses

## Bid-request

### POST

Bid information are passed to your bid-servers via JSON in the request body.
```example json request body
{
    request_id: 3,
    params: {
    	zoneid: 312
    }
    size: [[300, 250], [300, 100]],
    referrer: 'https://previous.page.com'
    ...
}
``` 

### GET

Bid parameters are passed by querystring. All querystring key-values are encoded via the `encodeURIComponent` method. It is worth noting that only a single size will be requested via the GET method.
```example querystring
http://example.bid.server.com?cb=234567246&request_id=3&width=300&height=250&referrer=https%3A%2F%2Fprevious.page.com...

```
`cb` is a random number that acts as a cachebuster.

### Bid information/parameters

|Name|Scope|Description|Example|
|---|---|---|---|
|channelid|required|The channel ID from integration partner| 3345678 |
|cb|required|Cache buster|86654516519|
[I THINK THERE IS MUCH MORE]

## Bid-response

We expect your bid-response to be in JSON with the following format.

```example response
{
    request_id: 3,
    cpm: 0.1218,
    ad: '<div>some example ad</div>'
}

```

### Bid-response parameters 

|Name|Scope|Description|Example|
|---|---|---|---|
|request_id|required|the request_id, used to tie this bid back to the request| 3 |
|cpm|required|The cpm of return creative, USD| 0.1218 |
|ad|required|The html snippet which can render ad|'`<div>some example ad</div>`'|

## A full example of the bid-request JSON

```example full json request body
{
    request_id: 3,
    params: {
    	zoneid: 312
    }
    size: [[300, 250], [300, 100]],
    referrer: 'https://previous.page.com',
    [COMPLETE THIS]
}
``` 