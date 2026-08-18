
2026-07-16

Tags: [[Designing Data Intensive Applications]] [[Data]] [[Databases]]
# Triple-Store Database Model
This model is functionally equivalent to the graph model, however it instead stores data in a simple textual format with each row having a (Subject, Predicate, Object). This Object can either be a primitive datatype or another node in the graph.

## Example
```Turtle
@prefix : <urn:example:>.
_:lucy a :Person.
_:lucy :name "Lucy".
_:lucy :bornIn _:idaho.
_:idaho a :Location.
_:idaho :name "Idaho".
_:idaho :type "state".
_:idaho :within _:usa.
_:usa a :Location.
_:usa :name "United States".
_:usa :type "country".
_:usa :within _:namerica.
_:namerica a :Location.
_:namerica :name "North America".
_:namerica :type "continent".
```


# References
- 