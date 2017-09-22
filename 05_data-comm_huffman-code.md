## Question:
A message has 1000 symbols A, B, C and D which the probability of occurrence of each symbol is 1/3, 1/2, 1/12 and 1/12 respectively. <br>

|S<sub>i</sub>|P<sub>i</sub>|log<sub>2</sub>(1/P<sub>i</sub>)|
|:---:|:---:|:---:|
|A|1/3|1.58 bits|
|B|1/2|1 bit|
|C|1/12|3.58 bits|
|D|1/12|3.58 bits|

- The fixed-length encoding use 2 binary digits for each symbol, then transmit the message (1000 symbols) needs 2000 binary digits. <br>
- The entropy of these symbols is: 1/3 * 1.58 + 1/2 * 1 + 1/12 * 3.58 + 1/12 * 3.58 = 1.626 bits.

__Can we find an encoding where transmitting the message (1000 symbols) in 1626 binary digits in average?__

# Optimal Code
__Our goal of _Source Coding_ is to produce as few bits as possible__

One of the goal of communication system is efficient sharing of the communication links among different users or conversations, so the ability to send data as few bits as possible is necessary.

> __Expected code length__
> Given _N_ symbols, with symbol _i_ occurring with probability _p<sub>i</sub>_, if we have a code in which symbol _i_ has length _l<sub>i</sub>_ in the code tree (i.e., the codeword is _l<sub>i</sub>_ bits long), then the expected length of the code, _L_, is &Sigma;{_i_=1:_N_} _p<sub>i</sub>l<sub>i</sub>_.

Shannon showed the _expected code length_ of any uniquely decodable code cannot be smaller then the _entropy, H_ of the symbols. Thus an _optimal code_ will have an _expected code length_ that matches the _entropy_ for the messages.

__The _Optimal Code_ is 
