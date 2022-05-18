# Exercises
keywords: #datalinklayer #networks

### Parity Related Questions

```
1- To provide more reliability than a single parity bit can give, an error-detecting coding scheme uses one parity bit for checking all the odd-numbered bits and a second parity bit for all the even-numbered bits. What is the Hamming distance of this code?
```

Although the first parity bit can detect even-numbered bits and the second parity bit can detect odd-numbered bits, this coding scheme can only detect ALL single error for sure, that is, d=1. Therefore, the Hamming distance is d+1=2. Although it can sometimes detect 2 errors (one even-numbered, one odd-numbered), it cannot detect all the 2 errors.

Review [[Hamming Distance]]

```
2- Sixteen-bit messages are transmitted using a Hamming code. How many check bits are needed to ensure that the receiver can detect and correct single-bit errors? Show the bit pattern transmitted for the message 1101001100110101. Assume that even parity is used in the Hamming code.
```

```
3- One way of detecting errors is to transmit data as a block of n rows of k bits per row and add parity bits to each row and each column. The bitin the lower-right corner is a parity bit that checks its row and its column. Will this scheme detect all single errors? Double errors? Triple errors? Show that this scheme cannot detect some four-bit errors.
```