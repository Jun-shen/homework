# Shannon–Fano Coding

## Example 1
|x<sub>i</sub>|P(x<sub>i</sub>)|Step 1|Step 2|Step 3|Step 4|Code|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|x<sub>1</sub>|0.30|0|0|||00|
|x<sub>2</sub>|0.25|0|1|||01|
|x<sub>3</sub>|0.20|1|0|||10|
|x<sub>4</sub>|0.12|1|1|0||110|
|x<sub>5</sub>|0.08|1|1|1|0|1110|
|x<sub>6</sub>|0.05|1|1|1|1|1111|

__Expected code length (L) = 2.38 bits/symbol__

__Entropy (H) = 2.36 bits/symbol__

## Code Efficiency = H / L
__H/L = 2.36/2.38 = 0.99__

# Shannon–Fano Algorithm
1. List the source symbols in order of decreasing probability.
2. Partition the set into two sets that areas close to equiprobables as possible and assign 0 to the upper set and 1 to the lower set.
3. Continue this process, each time partitioning the sets with as nearly equal probabilities as possible until further partitioning is not possible.
4. Assign codeword by appending the 0s and 1s from left to right.

## Example 2
|x<sub>i</sub>|P(x<sub>i</sub>)|Step 1|Step 2|Step 3|Step 4|Code|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|x<sub>1</sub>|0.30|0|0|||00|
|x<sub>2</sub>|0.25|0|1|||01|
|x<sub>3</sub>|0.10|1|0|0||100|
|x<sub>4</sub>|0.10|1|0|1|0|1010|
|x<sub>5</sub>|0.10|1|0|1|1|1011|
|x<sub>6</sub>|0.10|1|1|0||110|
|x<sub>7</sub>|0.10|1|1|1|0|1110|
|x<sub>8</sub>|0.10|1|1|1|1|1111|

__Expected code length (L) = 0.3*2 + 0.25*2 + 0.1*3 + 0.1*4 + 0.1*4 + 0.1*3 + 0.1*4 + 0.1*4 = 3.3 bits/symbol__

__Entropy (H) = 0.3 * 1.736 + 0.2 * 2.236 + 0.1 * 3.165 + 0.1 * 3.165 + 0.1 * 3.165 + 0.1 * 3.165 + 0.1 * 3.165 = 2.55 bits/symbol__

__Code Efficiency (H/L) = 2.55/3.3 = 0.77__

### Question: Compare to this Huffman code [example](https://github.com/cnchenpu/data-comm/blob/master/05_data-comm_huffman-code.md#example).
