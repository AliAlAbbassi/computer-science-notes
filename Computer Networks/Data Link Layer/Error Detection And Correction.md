# Error Detection And Correction

Access Index:
- [[Error Detection And Correction#Summary]]
- [[Data Link Layer Exercises#Parity Related Questions]]

### Parity
##### Summary
- It is a concept to detect errors
- A single bit error can be detected using this
- You have a transmitter and a reciever. Transmitter transmits some bit stuff
- A bit stream is sent with an extra bit, which represents the total number of 1s in the transmitter signal
- Concatenate the "Transmitter Signal" + "Parity Bit"
- There's two types of parity, Even and Odd

In Even Parity, parity bit equals 1 when you have odd number of 1s and equals 0 when you have even number of 1s. It's reversed for Odd Parity. 

Even Parity: 
```
Transmitter Signal: 0100
Parity Bit: 1
Output: 01001
```

Odd Parity: 
```
Transmitter Signal: 0100
Parity Bit: 0 
Output: 01000
```

###### But how do you use this to detect errors?
Consider the first example with even parity. Because of noise we recieved the following binary number from the transmitter
```
Transmitter Signal: 0101
Parity Bit: 1
Output: 01011
```

It has an even number of 1s, but it's parity bit is equal to 1, which usually represents the existence of odd number of 1s. So we conclude it's an error.
