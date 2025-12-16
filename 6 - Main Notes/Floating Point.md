
2025-08-25      // another one that I learned well before these notes

Tags: [[Computer Architecture]] [[Data]] 
# Floating Point
> Floating point allows us to represent very large numbers by not maintaining a continuous sequence of bits the way two's complement does, instead floats represent numbers similar to scientific notation ex: 1.363 * 10^33.

|        | Sign  | Exponent | Fraction |
| ------ | ----- | -------- | -------- |
| Single | 1 bit | 8 bits   | 23 bits  |
| Double | 1 bit | 11 bits  | 52 bits  |
In this format the fraction **must** stay between 1.0 and 2.0 as required by scientific notation, although something kind of neat is that since we use binary we don't need to include this number since it will always be 1.

## Single Bit Precision Range
**Smallest**
- Set the exponent to 0000_0001 and fraction to 00...00 so the significand is 1
- value = $1.0*2^{-126} \approx \pm 1.175 \cdot 10^{-38}$
**Largest**
- Set the exponent to 1111_1110 and fraction to 111...11
- value = $2.0 \cdot 2^{127} \approx \pm 3.4 \cdot 10^{38}$

# References
[[two's complement]]
