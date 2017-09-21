# The meaning of entropy for communication 
- Entropy (in bits) tells the average amount of information (in bits) that must be delieved in order to resolve the uncertainty about the outcome of a message.
- If send not enough bits, the receiver will have some uncertainty in the message.
- If send two much bit, we will wast the capacity of the communication channel.

# The digital communication system model
- Communication systems convert the source output into a binary sequence and then convert that binary sequence into a form suitable for transmission over particular physical media such as cable, twisted wire pair, optical fiber, or electromagnetic radiation through space.
- Digital communication systems use digital sequence as an interface between the source and the channel input and between the channel output and final destination.
- The source encoder converts the source output to a binary sequence and the channel encoder (often called a modulator) processes the binary sequence for transmission over the channel. The channel decoder (demodulator) recreates the incoming binary sequence (hopefully reliably), and the source decoder recreates the source output.

![](fig/digi-comm-1.png)

__EX: The communication system for waveform information__
- The source coding/decoding layer can be split into 3 layers:
    - sampler/analog filter
        - The input side of the outermost layer converts the waveform into a sequence of samples and output side converts the recovered samples back to the waveform.
    - quantizer/table lookup
        - The quantizer converts each sample into one of a finite set of symbols, and the peer module recreates the sample.
    - discrete encoder/decoder
        - To encode the sequence of symbols into binary digits and decode vice versa.
        
![](fig/digi-comm-2.png)

# The Source Coding
- A conversion of a discrete memory less source (DMS) into a sequence of binary symbols.
    - DMS: independent probability
- To minimize the average bit rate required for representation of the source by reducing the redundancy of the information source.

# Classification of Code:
- Fixed Length Codes
    - Code word length is fixed.
- Variable Length Codes
    - Code work lenght is not fixed.
- Distinct Codes
    - Each code word is distinguishable from each other. 
- Prefix Free Codes
    - No code word is prefix of another.
- Uniquely Decodable Codes
    - A distinct code is uniquely decodable if the original source sequece can be reconstructed from the encoded sequence.
- Instantaneous Codes
    - A uniquely decodable code if the end of any code word is recognizable without examining subsequence code symbols. (Prefix Free Codes)
- Optimal Codes
    - An instantaneous code and has the minimum average length for a given source.

__EX:__

|Xi|Code 1|Code 2|Code 3|Code 4|Code 5|Code 6|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|X1|00|00|0|0|0|1|
|X2|01|01|1|10|01|01|
|X3|00|10|00|110|011|001|
|X4|11|11|11|111|0111|0001|

