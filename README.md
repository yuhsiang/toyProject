# [Insert name of the project]

This README is for developers who wish to make a request to integrate their frontend ad bidders with [CONFIRM NAME].

Following are steps for guiding you to making the integration.
1. Design your bid-request params
2. Decide your bid request endpoint url, and request method (GET or POST)
3. Implement the bid response
4. Copy and fill the technical form from [SOME TO BE ADDED URL] and send it to [SOME EMAIL, PROBABILY MARKETING PEOPLE].

# Requirements

* Bid-request endpoints must support HTTPS
* The returned ad and all resources must also support HTTPS
* Bid-response must be AJAX with JSON responses

## Bid-request

### POST

Bid information are passed to your bid-servers via JSON in the request body.
```example json request body
{
    request_id: "32itdo54o7",
    params: {
    	channel_id: 312,
      web_id: "urx54u"
    }
    size: [[300, 250], [300, 100]],
    url: "https://current.page.com",
    referrer: "https://previous.page.com"
    ...
}
```

The `params` object is the place to put all parameters needs for your bid servers to make the bid. Only `string` and `number` type is supported as parameters.

### GET

Bid parameters are passed by querystring. All querystring key-values are encoded via the `encodeURIComponent` method. It is worth noting that only a single size will be requested via the GET method.
```example querystring
http://example.bid.server.com?cb=234567246&request_id=3&width=300&height=250&referrer=https%3A%2F%2Fprevious.page.com...

```
`cb` is a random number that acts as a cachebuster.


### Bid information/parameters

|Name|Type|Description|Example|POST|GET|
|---|---|---|---|---|---|
| request_id| string | the request_id, used to tie this bid request to the response | `32itdo54o7` | v | v |
| cb | number | cache buster | `86654516519` | | v |
| width | number | width of ad slot in px | `300` | | v |
| height | number | height of ad slot in px| `250` | | v |
| size | array | allowed size for this ad slot, array of arrays, the inner array will always have two numbers, the first is the width and the second is the height | `[[300, 250], [300, 100]]` | v | |
| url | string | url of the web page | `https://url.com` | v | v |
| referrer | string | referrer of the referrer | `https://referrer.com` | v | v |
| interstitial | true/false | whether this is an interstitial ad slot or not | `true` | v | v |
| atf | true/false | whether this ad slot is above the fold or not | `true` | v | v |

## Bid-response

We expect your bid-response to be in JSON with the following format.

```example response
{
    request_id: "32itdo54o7",
    cpm: 0.1218,
    ad: "<div>some example ad</div>"
}

```

### Bid-response parameters 

|Name|Type|Description|Example|
|---|---|---|---|
| request_id | string | the request_id, used to tie this bid back to the request| `32itdo54o7` |
| cpm | number | The cpm of the bid, USD | `0.1218` |
| ad | string | The html snippet of your ad | `<div>some example ad</div>` |

## A full examples of the POST bid-request JSON

```A full examples of the POST bid-request JSON
{
    request_id: 3,
    params: {
    	channel_id: 312,
      web_id: 246
    }
    size: [[300, 250], [300, 100]],
    url: 'https://current.page.com',
    referrer: 'https://previous.page.com',
    interstital: false,
    atf: true
}
``` 

## A full example of the GET querystring

```A full example of the GET querystring
https://example.bidder.com?cb=23465276&width=300&height=250&interstital=false&atf=true&channel_id=312&web_id=246&url=https%3A%2F%2Fcurrent.page.com&referrer=https%3A%2F%2Fprevious.page.com

``` 
