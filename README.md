# [Insert name of the project]

This README is for developers who wish to make a request to integrate their frontend ad bidders with [CONFIRM NAME].

Following are steps for guiding you to making the integration. 
1. Decide your bid request endpoint url, and request method
2. Implement the bid response
3. Copy and fill the technical form from [SOME TO BE ADDED URL] and send it to [SOME EMAIL, PROBABILY MARKETING PEOPLE].

# Requirements

* Bid-request endpoints must support HTTPS 
* Bid-response must be AJAX with JSON responses

## POST request

Bid information are passed to your bid-servers via JSON in the request body.
```example json request body
{
	request_id: 3,
	size: [[300, 250], [300, 100]],
    ...
}
``` 

## GET request

Bid parameters are passed by query strings. 
```example querystring
http://example.bid.server.com?cb=234567246&request_id=3&width=300&height=250&

```
`cb` is a random number that acts as a cachebuster.
  