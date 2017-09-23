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

__Expected code length__

Given _N_ symbols, with symbol _i_ occurring with probability _p<sub>i</sub>_, if we have a code in which symbol _i_ has length _l<sub>i</sub>_ in the code tree (i.e., the codeword is _l<sub>i</sub>_ bits long), then the expected length of the code, _L_, is &Sigma;{_i_=1:_N_} _p<sub>i</sub>l<sub>i</sub>_.

Shannon showed the _expected code length_ of any uniquely decodable code cannot be smaller then the _entropy, H_ of the symbols. Thus an _optimal code_ will have an _expected code length_ that matches the _entropy_ for the messages.

# Huffman Code
- David Huffman (1951)
- Use shorter bit sequence for high probability symbol, longer sequences for less probale symbol.

|S<sub>i</sub>|P<sub>i</sub>|Code|
|:---:|:---:|:---:|
|A|1/3|10|
|B|1/2|0|
|C|1/12|110|
|D|1/12|111|

Expected length = 1/3 * 2 + 1/2 * 1 + 1/12 * 3 + 1/12 * 3 = 1.666 bits

Transmitting the message (1000 symbols) in 1666 binary digits in average __(not optimal)__.

- How to build the code tree:
    1. S = {(A, 1/3), (B, 1/2), (C, 1/12), (D, 1/12)}
    2. S = {(A, 1/3), (B, 1/2), (CD, 1/6)}
    3. S = {(B, 1/2), (ACD, 1/2)}
    4. S = {(BACD, 1)}
    
&nbsp;&nbsp;&nbsp;&nbsp;CD <br>
&nbsp;&nbsp;0/&nbsp;&nbsp;\1 <br>
&nbsp;&nbsp;C&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;D <br>

&nbsp;&nbsp;&nbsp;ACD <br>
&nbsp;&nbsp;0/&nbsp;&nbsp;&nbsp;\1 <br>
&nbsp;A&nbsp;&nbsp;&nbsp;0/&nbsp;&nbsp;\1 <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;C&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;D <br>

&nbsp;&nbsp;0/&nbsp;&nbsp;&nbsp;\1 <br>
&nbsp;B&nbsp;&nbsp;&nbsp;0/&nbsp;&nbsp;\1 <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A&nbsp;&nbsp;&nbsp;0/&nbsp;&nbsp;\1 <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;C&nbsp;&nbsp;&nbsp;&nbsp;D <br>

- Huffman Code Algorithm
    1. Begin with the set of symbols __S__, put the probability __p(s)__ for each __s__ in __S__.
    2. Repeat the following steps until there is only 1 symbol left in __S__:
    3. Choose two members __(s<sub>i</sub>, s<sub>j</sub>)__ from __S__ which have lowest probabilities.
    4. Remove the selected symbols from __S__, and create a new node of the code tree whose childen are the symbols you have removed __(s<sub>i</sub>, s<sub>j</sub>)__. Label the left sibling with code __0__, and the right sibling with code __1__.
    5. Add a new symbol into __S__ that represent this new node and combine their probabilities (__p(s<sub>i</sub>) + p(s<sub>j</sub>)__).

# Homework (due date: 10/2)
2. Consider following symbols, compute __a)__ the Huffman code, __b)__ draw the code tree, __c)__ the average code length, and __d)__ the entropy of the code. <br>
{(A, 0.25), (B, 0.25), (C, 0.125), (D, 0.125), (E, 0.125), (F, 0.0625), (G, 0.0625)}

# Program Project (due date: 10/16)
- Use any programming language you like to output the Huffman code of Homework 2.
    - Input: {(A, 0.25), (B, 0.25), (C, 0.125), (D, 0.125), (E, 0.125), (F, 0.0625), (G, 0.0625)}
    - Output: The Huffman code for each symboles.
- Bonus 1: Draw the code tree.
- Bonus 2: A general purpose version of Huffman code generater, i.e. user can input a finite set of symbols and their probabilities, then output their Huffman codes.
- Your work have to submit to your github which includes source code, outputs and a brief of your ideas in README.
