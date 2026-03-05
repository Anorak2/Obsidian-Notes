Status: 

Tags: [[Data Structures]]
# Arrays

An array is a fixed block of memory that is characterized by having an incredibly fast speed retrieval, O(1). We can do this by returning the memory address of head + the index * the size of the box

| 0   | 1   | 2   | 5   | 62  |
| --- | --- | --- | --- | --- |
 ^
head

With these being Uint8s, we could just do arr[i] = head + i * 8

# References

