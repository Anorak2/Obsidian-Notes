Status: 

Tags: [[Algorithms]] 
# Hashing

Hashing is pretty awesome, what it allows us to do is generate unique values for input data as long as we stay within a certain range of input values. 

**In Practice**
How we generate hashes in practice is we first find the size of the set of characters that we could input. If we were only using say, lower case letters then it would be 26, and to be larger we need to us 27

We can then hash a word by doing this type of function
$$(a  \cdot 27^2) + (b \cdot 27^1)+(c \cdot 27^0)$$
Using a function with this pattern means that we can **never** have a collision, although in practice we can since we use modulus to ensure a certain size. This works because we are converting our number system from base 10 to base 27, and this allows us to assign a digit to exactly one number. What is even cooler is that the operation is obscured which is why hashes are often used for security reasons.

It also doesn't matter than we convert it back to base 10, since the number in base 10 has the same value as it does in base 27. The part that matters is how we assign that number.

# References

[[Hash Tables]]