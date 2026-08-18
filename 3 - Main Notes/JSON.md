

2026-07-01

Tags:  [[Software Engineering (SWE)]]
# JavaScript Object Notation
JSON is a lightweight, relatively fast format that is native to javascript and is commonly used in web projects or by API's. This is because it has wide support and is human readable, allowing for easy debugging.

pros:
- lightweight and compact
- native to javascript
- fast
- widely supported

cons:
- no comments allowed
- limited data types supported, including no date/time type
- strict syntax (when not machine generated)
## Example
```javascript
{
  "user": {
    "id": 12345,
    "name": "John Doe",
    "email": "john@example.com",
    "isActive": true,
    "roles": ["admin", "developer"],
    "address": {
      "street": "123 Main St",
      "city": "San Francisco",
      "zipCode": "94102"
    }
  }
}
```


# References
- 