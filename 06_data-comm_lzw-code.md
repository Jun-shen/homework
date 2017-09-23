# Lempel-Ziv-Welch (LZW) Algorithm
- Lempel-Ziv-Welch (1977,’78,’84)
- Adaptive variable-length coding.
- Don't need the statistic (probability) infomation of the source.
- Build a dictionary for sequential strings of symbols encountered in the source text.
- Compress streaming text to sequence of __dictionary address (index)__, the __codeword__ sent to the receiver.
- Variable length source strings assigned to fixed length dictionary addresses.
- Starting from an agreed core dictionary of symbols, receiver builds up a dictionary that mirrors the sender's, with a one-step delay, and use this to exactly recover the source text (lossless).
- As message is processed, encoder builds a "string table" that maps symbol sequences to an N-bits fixed-length code. 
    - __Table size = 2<sup>N</sup>__.
    
## Example

abcabcabcabcabcabcabc

Use 8 bits for coding, the table size is 2<sup>8</sup>=256.

Initialize table: first 256 entries (0 ~ 255) hold ASCII codes of symbol.

|Current|Next|Output|Add to dictionay|Comments|
|:---:|:---:|:---:|:---:|:---|
|a 97|b 98|a 97|ab 256|add 'ab' to table|
|b 98|c 99|b 98|bc 257|add 'bc' to table|
|c 99|a 97|c 99|ca 258|add 'ca' to table|
|a 97|b 98|-|-|'ab' exists in table,<br>check if 'abc' in table|
|ab 256|c 99|ab 256|abc 259|add 'abc' to table|
|c 99|a 97|-|-|'ca' exists in table,<br>check if 'cab' in table|
|ca 258|b 98|ca 258|cab 260|add 'cab' to table|
|b 98|c 99|-|-|'bc' exists in table,<br>check if 'bca' in table|
|bc 257|a 97|bc 257|bca 261|add 'bca' to table|
|a 97|b 98|-|-|'ab' exists in table,<br>'abc' exists in table,<br>check if 'abca' in table|
|abc 259|a 97|abc 259|abca 262|add 'abca' in table|
|a 97|b 98|-|-|'ab' exists in table,<br>'abc' exists in table,<br>'abca' exist in table, <br>check if 'abcab' in table|
|abca 262|b 98|abca 262|abcab 263|add 'abcab' in table|
|b 98|c 99|-|-|'bc' exists in table,<br>'bca' exist in table,<br>check if 'bcab' in table|
|bca 261|b 98|bca 261|bcab 263|add 'bcab' to table|
|b 98|c 99|-|-|'bc' exist in table|
|bc 257|-|bc 257|-|end|

