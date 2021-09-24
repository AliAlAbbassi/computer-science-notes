# The Physical Layer
keywords: #computernetworks #computerscience 
### Objectives
- Theoretical Basis for Data Communication
- Guided Transmission
- Wireless Transmission
- Digital Modulation and Multiplexing

The Physical layer is the foundation on which other layers are build.
Modulation means transforming digital bits using only analog signals.

###### Data can be analog or digital
- Analog data is continous (rich in artifacts and information)
- Analog signals can have an infinte number of values in a range
- Digital data has discrete states
- Digital signals can have a limited number of values in a range

###### Periodic Analog Signals
can be classified as simple or composite
- A simple periodic analog signal, a sine wave, cannot be decomposed into simpler singals.
- A composite periodic analog signal is composed of mutliple sine waves.

###### Frequency
- A signal that doesn't change at all has a frequency of zero
- A signal that changes instantaneously, has infinite frequency
```
F= 1/T and T = 1/F
```

The frequency domain is more compact and useful when we are dealing with more than one sine wave
A single-freq sine wave isn't useful in data communication. We need to send a composite signal.

#### Fourier Analysis
Jean-Baptiste Fourier proved that any reasonably behaved periodic function, g(t) with period T, can be constructed as the sum of a (possibly infinite) number of sines and cosines:
![](https://cdn.discordapp.com/attachments/845561994022879264/890703901827928074/unknown.png)
where f = 1/T is the fundamental frequency, an and bn are the sine and cosine amplitudes of the nth harmonics (terms), and c is a constant. Such a decomposition is called a Fourier series. From the Fourier series, the function can be reconstructed. That is, if the period, T, is known and the amplitudes are given, the original function of time can be found by performing the sums of Eq. (2-1). 
A data signal that has a finite duration, which all of them do, can be handled by just imagining that it repeats the entire pattern over and over forever (i.e., the interval from T to 2T is the same as from 0 to T, etc.). 

#### Bandwidth-Limited Signals
The relevance of all of this to data communication is that real channels affect different frequency signals differently.

The width of the frequency range transmitted without being strongly attenuated is called the bandwidth.

The bandwidth is a physical property of the transmission medium that depends on, for example, the construction, thickness, and length of a wire or fiber. Filters are often used to further limit the bandwidth of a signal. 802.11 wireless channels are allowed to use up to roughly 20 MHz, for example, so 802.11 radios filter the signal bandwidth to this size. As another example, traditional (analog) television channels occupy 6 MHz each, on a wire or over the air. This filtering lets more signals share a given region of spectrum, which improves the overall efficiency of the system. It means that the frequency range for some signals will not start at zero, but this does not matter. The bandwidth is still the width of the band of frequencies that are passed, and the information that can be carried depends only on this width and not on the starting and ending frequencies. Signals that run from 0 up to a maximum frequency are called baseband signals. Signals that are shifted to occupy a higher range of frequencies, as is the case for all wireless transmissions, are called passband signals. 

(digital) bandwidth is the maximum data rate of a channel, a quantity measured in bits/sec. That data rate is the end result of using the analog bandwidth of a physical channel for digital transmission, and the two are related, as we discuss next.

#### Guided Transmission Media
The purpose of the physical layer is to transport bits from one machine to another.

###### Magnetic Media
One of the most common ways to transport data from one computer to another is to write them onto magnetic tape or removable media (e.g., recordable DVDs), physically transport the tape or disks to the destination machine, and read them back in again. Although this method is not as sophisticated as using a geosynchronous communication satellite, it is often more cost effective, especially for applications in which high bandwidth or cost per bit transported is the key factor.

###### Twisted Pairs
Although the bandwidth characteristics of magnetic tape are excellent, the delay characteristics are poor. Transmission time is measured in minutes or hours, not milliseconds. For many applications an online connection is needed. One of the oldest and still most common transmission media is twisted pair. A twisted pair consists of two insulated copper wires, typically about 1 mm thick. The wires are twisted together in a helical form, just like a DNA molecule. Twisting is done because two parallel wires constitute a fine antenna. When the wires are twisted, the waves from different twists cancel out, so the wire radiates less effectively. A signal is usually carried as the difference in voltage between the two wires in the pair. This provides better immunity to external noise because the noise tends to affect both wires the same, leaving the differential unchanged.

Twisted pairs can be used for transmitting either analog or digital information.

Twisted-pair cabling comes in several varieties. The garden variety deployed in many office buildings is called Category 5 cabling, or ‘‘Cat 5.’’ A category 5 twisted pair consists of two insulated wires gently twisted together. Four such pairs are typically grouped in a plastic sheath to protect the wires and keep them together

###### Link Terminology
Some general terminology is now in order. Links that can be used in both directions at the same time, like a two-lane road, are called full-duplex links. In contrast, links that can be used in either direction, but only one way at a time, like a single-track railroad line. are called half-duplex links. A third category consists of links that allow traffic in only one direction, like a one-way street. They are called simplex links.

Through Category 6, these wiring types are referred to as UTP (Unshielded Twisted Pair) as they consist simply of wires and insulators

### Digital Modulation and Multiplexing
Wires and wireless channels carry analog signals such as continuously varying voltage, light intensity, or sound intensity.
To send digital information, we must devise analog signals to represent bits.
The process between converting between bits and signals that represent them is called digital modulation.

<u>Modulation</u> schemes send bits as signals
<u>Multiplexing</u> schemes share a channel among users.