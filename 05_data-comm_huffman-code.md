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
