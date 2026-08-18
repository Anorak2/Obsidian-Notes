
2026-07-01

Tags: [[Data Structures]] 
# Extensible Markup Language
XML is a markup language used for storing, transmitting, and reconstructing data. It is used for encoding documents that are both human readable and machine readable. It's design goals are to emphasize simplicity, generality, and usability across the internet.

It has strong support for unicode characters for different languages, and is often used for arbitrary data structures for web services much like JSON.

XML is best used when strict validation is required, for document markup like HTML or RSS feeds, or for complex documents where metadata and attributes matter.

**pros:**
- self descriptive tags
- XML allows for comments 
- XML supports attributes
- and is excellent for documents

**cons:**
- it is very verbose
- has larger file sizes due to html like tags
- slower parsing
- more complex to write

## Example
```xml
<?xml version="1.0" encoding="UTF-8"?>
<user>
  <id>12345</id>
  <name>John Doe</name>
  <email>john@example.com</email>
  <isActive>true</isActive>
  <roles>
    <role>admin</role>
    <role>developer</role>
  </roles>
  <address>
    <street>123 Main St</street>
    <city>San Francisco</city>
    <zipCode>94102</zipCode>
  </address>
</user>
```

# References
-  [[JSON]]