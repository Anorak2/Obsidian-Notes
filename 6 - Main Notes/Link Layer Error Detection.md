
2025-11-20

Tags: [[Networking]]
# Link Layer Error Detection
At the link layer error detection has to be added, with a section of data (D) and a section for ensuring validity (EDC) for error detection and correction. Conceptually this works because we map "data words" into a larger space where they become separated.

**Block Codes:** each d consequent data bits map to a c bit code word 
- Rate of a (c,d) block code = d/c
- Redundancy = c - d bits per d data bits
- Hamming distance: the number of differing bits between two code-words  
- Minimal distance: Hamming distance between two closest code-words  
- Theorem: If the minimal distance of a code is h, then it is possible to detect up to h-1 errors.

## Parity Checking
---
Single Bit Parity:  
- Even parity: Add one additional bit and choose its value such that the total number of 1s in the d + 1 bits is even.  
- Detect single bit errors

Two Dimensional Bit Parity:
- This version is capable of detecting and correcting single bit errors by cross referencing the parity bits for that row/column.
# References
