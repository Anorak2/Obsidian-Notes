
2024-12-24

Status:

Tags: [[Programming]] [[Web]]
# HTTP status codes
```1XX```
This category is reserved for informational requests, and for the most part you just shouldn't use this category except when experimenting.

```2XX```
These are various types of success codes, where each of the sub codes is informing about the state of the server. An example would be 202 for accepted, or 208 already reported.

```3XX```
These are redirection codes, which means the client must take some kind of additional action to  complete the request. These codes are often used for redirecting to a different website.

```4XX```
This type of error is for client codes where there was some kind of error that was seemingly caused by the client. Common types include 403 forbidden or 404 for not found but there are a lot of codes.

```5XX```
These are errors that happen on the server side of thing, this includes 500 internal server error, 502 bad gateway, and 503 service unavailable
# References
[[HTTP]]


