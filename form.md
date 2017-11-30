# General Information

Company Name:

Maintainer(email):

# Bid request

Bid-request endpoint url: 

Method of Request(GET/POST):

Location of your bid servers(list all possible locations): 

## Bid request params

|Name|Type|Description|Example|
|---|---|---|---|
| request_id| string | the request_id, used to tie this bid request to the response | `32itdo54o7` |
| cb | number | cache buster | `86654516519` |
| width | number | width of ad slot in px | `300` |
| height | number | height of ad slot in px| `250` |
| size | array | allowed size for this ad slot, array of arrays, the inner array will always have two numbers, the first is the width and the second is the height | `[[300, 250], [300, 100]]` |
| url | string | url of the web page | `https://url.com` |
| referrer | string | referrer of the referrer | `https://referrer.com` |
| interstitial | true/false | whether this is an interstitial ad slot or not | `true` |
| atf | true/false | whether this ad slot is above the fold or not | `true` |

