# Communication Network Abstrication
![](/fig/digi-comm-2.png)
__Packets -> Bits -> Signals -> Bits -> Packets__

# Analog signal is nature
- Transmitting over a wire, we can send dignal at different voltage levels, and the receiver can measure the voltage to determine what the sender transmitted. <br> EX:
    - Black-and-white analog TV use the voltage waveform to represt the shade of gray of the picture.
    - Analog phone convert sound wave to electrical signal and back.
- Transmitting over an optical communication link, we can send signal in different intensities and/or wavelength.

# Channel Capacity
Channel Capacity is defined as the maximum amount information a channel can convey per unit time. 

## Data Rate Limits
The maximum data rate limit over a medium is decided by followinf factors:
- Bandwidth of channel
- Signal levels
- Channel quality (level of noise)

## Shannon Capacity (Noisy Channel)
__C = BW * log<sub>2</sub>(1+S/N)__

where:
- C: Channel capacity (bits per second)
- BW: Bandwidth of channel
- S/N: signal to noise ratio
