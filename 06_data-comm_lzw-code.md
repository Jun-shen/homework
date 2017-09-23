# Lempel-Ziv-Welch (LZW) Compress Coding
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
- source: abbbabbbab

Use 8 bits for coding, the table size is 2<sup>8</sup>=256.

Initialize table: first 256 entries (0 ~ 255) hold ASCII codes of symbol.

|Current|Next|Output|Add to dictionay|Comments|
|:---:|:---:|:---:|:---:|:---|
|a 97|b 98|a 97|ab 256|'ab' not exist, add it to table|
|b 98|b 98|b 98|bb 257|'bb' not exist, add it to table|
|b 98|b 98|-|-|'bb' exist in table, 'bba' not exist|
|bb 257|a 97|bb 257|bba 258|add 'bba' to table|
|a 97|b 98|-|-|'ab' exist in table, 'abb' not exist|
|ab 256|b 98|ab 256|abb 259|add 'abb' to table|
|b 98|b 98|-|-|'bb' exist in table, 'bba' exist to, 'bbab' not|
|bba 258|b 98|bba 258|bbab 260|add 'bbab' to table|
|b 98|-|b 98|-|end|

- code: 97, 98, 257, 256, 258, 98.

## Example
- source: abcabcabcabcabcabcabc

Use 8 bits for coding, the table size is 2<sup>8</sup>=256.

Initialize table: first 256 entries (0 ~ 255) hold ASCII codes of symbol.

- encode:

|Current|Next|Output|Add to dictionay|Comments|
|:---:|:---:|:---:|:---:|:---|
|a 97|b 98|a 97|ab 256|'ab' not exist, add it to table|
|b 98|c 99|b 98|bc 257|'bc' not exist, add it to table|
|c 99|a 97|c 99|ca 258|'ca' not exist, add it to table|
|a 97|b 98|-|-|'ab' exists in table, 'abc' not|
|ab 256|c 99|ab 256|abc 259|add 'abc' to table|
|c 99|a 97|-|-|'ca' exists in table, 'cab' not|
|ca 258|b 98|ca 258|cab 260|add 'cab' to table|
|b 98|c 99|-|-|'bc' exists in table, 'bca' not|
|bc 257|a 97|bc 257|bca 261|add 'bca' to table|
|a 97|b 98|-|-|'ab' exists in table, 'abc' exists too, 'abca' not|
|abc 259|a 97|abc 259|abca 262|add 'abca' in table|
|a 97|b 98|-|-|'ab' exists in table, so does 'abc' and 'abca', 'abcab' not|
|abca 262|b 98|abca 262|abcab 263|add 'abcab' in table|
|b 98|c 99|-|-|'bc' exists in table, bca' exist too, 'bcab' not|
|bca 261|b 98|bca 261|bcab 264|add 'bcab' to table|
|b 98|c 99|-|-|'bc' exist in table|
|bc 257|-|bc 257|-|end|

- code: 97, 98, 99, 256, 258, 257, 259, 262, 261, 257.

# LZW Algorithm

STRING = get input symbol <br>
__WHILE__ there are still input symbols __DO__ <br>
&nbsp;&nbsp;&nbsp;&nbsp;SYMBOL = get input symbol <br>
&nbsp;&nbsp;&nbsp;&nbsp;__IF__ STRING + SYMBOL is in the TABLE __THEN__ <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;STRING = STRING + SYMBOL <br>
&nbsp;&nbsp;&nbsp;&nbsp;__ELSE__ <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;output the code for STRING <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;add STRING + SYMBOL to TABLE <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;STRING = SYMBOL <br>
&nbsp;&nbsp;&nbsp;&nbsp;__END__ <br>
__END__ <br>
output the code for STRING <br>

## Homework (due date: 10/2)
Use LZW algorithm to encode "abcabcabcabcabcabcabcabcabcabcabcabc".
