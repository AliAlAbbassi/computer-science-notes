# Hamming Distance
keywords: #datalinklayer #errorcorrectingcode

It is an Error-Correcting code.

##### Error-Correcting Codes
*They* add redundancy to the information that is sent. A frame consists of m data (i.e., message) bits and r redundant (i.e. check) bits. 
In a block code, the r check bits are computed solely as a function of the m data bits with which they are associated, as though the m bits were looked up in a large table to find their corresponding r check bits. In a systematic code, the m data bits are sent directly, along with the check bits, rather than being encoded themselves before they are sent. In a linear code, the r check bits are computed as a linear function of the m data bits. Exclusive OR (XOR) or modulo 2 addition is a popular choice. This means that encoding can be done with operations such as matrix multiplications or simple logic circuits. The codes we will look at in this section are linear, systematic block codes unless otherwise noted.

To understand how errors can be handled, it is necessary to first look closely at what an error really is.

##### What is an Error?
Given two codewords that may be transmitted or recieved
```
10001001 and 10110001
```

It is possible to determine how many corresponding bits differ. In this case, 3 bits differ. To determine how many bits differ, just XOR the two codewords and count the number of 1 bits in the result. 
For example:
```
10001001 
10110001 
--------
00111000
```

##### So what is the hamming distance?
The number of bit positions in which two codewords differ is called the Hamming distance (Hamming, 1950). Its significance is that if two codewords are a Hamming distance d apart, it will require d single-bit errors to convert one into the other.

##### How to get the hamming distance if you have the algo
Given the algorithm for computing the check bits, it is possible to construct a complete list of the legal codewords, and from this list to find the two codewords with the smallest Hamming distance. This distance is the Hamming distance of the complete code.