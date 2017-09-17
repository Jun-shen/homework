__Claude Shannon__ (1916-2001)
- 1937, MIT EE master thesis "A symbolic analysis of relay and switching circuits", introduce Boolean algebra to logic circuits.
- 1948, Bell Lab, "A mathematical theory of communication".

![](fig/shannon_comm_channel.jpg)

# Probabilistic basis
- _Events_ are subsets of outcomes. Event defines probability.
- 0 &le; P(A) &le; 1
- P(A+B) = P(A) + P(B) if A and B are mutually exclusive, i.e. P(AB) = 0.
- P(A+B) = P(A) + P(B) - P(AB)
- Independent events: P(AB) = P(A)P(B)
- Conditional probability: P(A|B) = P(AB)/P(B)
- Expected value: probability weighted average.

# Information basis
- A communication system arm to transmit information from source to receiver. Each message conveys some information; some information conveys more information than other.
- The amount of information is the time of the message transmission, larger information spend more time to transfer.
- The amount of information depends on the probability of occurrence of the event.

       EX: 
       - The sum will rise in east tomorrow.
       - It will rain tomorrow.
        
> Information from intuitive point of view:
>
> If I is the amount of information of a message m and P is the probability of occurrence of that event then mathematically, 
>
> __I = 0; if P = 1,__
>
> __I = &infin;; if P = 0__
>
> To hold above relation, the relation between I and P will be,
>
> __I = log<sub>2</sub>(1/P)__   	
>
> In information theory base of the logarithmic function is 2.

> If communication source generate messages m<sub>1</sub>, m<sub>2</sub>, m<sub>3</sub>, ..., m<sub>k</sub> with probability of occurrence P<sub>1</sub>, P<sub>2</sub>, P<sub>3</sub>, ..., P<sub>k</sub>, and if the probability of messages are independent, then the probability of the composite message is
>
> __P = P<sub>1</sub>P<sub>2</sub>P<sub>3</sub>...P<sub>k</sub>__
>
> The information carried by the composite message is
>
> __I = log<sub>2</sub>(1/P)__
>
>   __= log<sub>2</sub>(1/P<sub>1</sub>P<sub>2</sub>P<sub>3</sub>...P<sub>k</sub>)__
>
>   __= log<sub>2</sub>(1/P<sub>1</sub>) + log<sub>2</sub>(1/P<sub>2</sub>) + ... + log<sub>2</sub>(1/P<sub>k</sub>)__
>
>   __= I<sub>1</sub> + I<sub>2</sub> + ... + I<sub>k</sub>__
>

The information __I__ is inverse to the probability __P__, less probability produce more information.

> Information from engineering view:
>
> The amount of information in a message is proportional to the time required to transmit the message. 
>
> Therefore the message with smaller probability of occurrence needs long code word and that of larger probability need shorter codeword. 

The more efficient communication system need to transmit more messages in a range of time (if the channel capacity _bits/sec_ is fixed), then we need to encode the message as less as possible. I.e. more probability event use smaller codeword; less probability event use larger codeword. More probability event has less information; less probability have more information.

__Central idea of information theory is that messages of a source has to be coded in such a way that maximum amount of information can be transmitted through the channel of limited capacity.__

