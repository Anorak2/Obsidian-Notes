
2025-08-25

Tags: [[Computer Architecture]] [[Data]] [[Programming]]
# two's complement
> Two's complement is a way to represent positive and negative numbers in a fixed amount of space. We can accomplish this by having a sign bit (0 if positive, 1 if negative), and then if our sign is 0 we can count from 0 -> 2^(n-1) just fine. However if we want to represent a negative number such as negative 1, it would look like 1_111 in 4 bit and in 8 bit -2 would be 1_111_1110. The negative numbers have a range of -1   -> -2^(n-1)

![[Pasted image 20250825152115.png]]

Addition and subtraction are done the same way as normal binary addition and subtraction, it also works to negate first and then add to do subtraction.

# References

