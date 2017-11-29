This README is for developers who wish to make a request to integrate their frontend ad bidders with [CONFIRM NAME]. Following are steps for guiding you for making the request. 

1. Decide your bid request endpoint url, and request method
2. Implement the bid response
3. Copy and fill the technical form from [SOME TO BE ADDED URL] and send it to [SOME EMAIL, PROBABILY MARKETING PEOPLE].

Requirements

* Both GET and POST HTTP request methods are supported. 

POST
Bid parameters are passed by JSON in the request body.
```example json request body
{
	request_id: 3,
	size: [[300, 250], [300, 100]],
    
}
``` 

GET
Bid parameters are passed by query strings. 
```example querystring
http://example.bid.server.com?request_id=3&width=300&height=250&

```

  