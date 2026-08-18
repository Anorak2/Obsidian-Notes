
2026-07-01

Tags:
# YAML
YAML is very human readable when compared to alternatives like JSON or XML. Comments are supported, and there are rich data types allowed. XML also supports anchors and references. The cons include indentation sensitive, slower parsing than JSON, complex specification.

As a result YAML is best for general configuration, including docker-compose and infrastructure as code.



## Example
```yaml
user:
  id: 12345
  name: John Doe
  email: john@example.com
  isActive: true
  roles:
    - admin
    - developer
  address:
    street: 123 Main St
    city: San Francisco
    zipCode: "94102"  # Quotes preserve leading zeros
```

# References
- [[JSON]]
- [[XML]]