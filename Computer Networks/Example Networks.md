# Example Networks

There's a lot of different networks that exists; here's a sneak peak!

### The Internet
The Internet is not really a network at all, but a vast collection of different networks that use certain common protocols and provide certain common services.

### The ARPANET
Here the black dots represent telephone switching offices, each of which was connected to thousands of telephones. These switching offices were, in turn, connected to higher-level switching offices (toll offices), to form a national hierarchy with only a small amount of redundancy. The vulnerability of the system was that the destruction of a few key toll offices could fragment it into many isolated islands

Paul Baran, came up with the highly distributed and fault-tolerant design of Fig. 1-25(b).

![](https://cdn.discordapp.com/attachments/845561994022879264/888838404698144810/unknown.png)

##### Arpanet: Packet Switching Network
The subnet would consist of minicomputers called IMPs (Interface Message Processors) connected by 56-kbps transmission lines. For high reliability, each IMP would be connected to at least two other IMPs. The subnet was to be a datagram subnet, so if some lines and IMPs were destroyed, messages could be automatically rerouted along alternative paths.

Each node of the network was to consist of an IMP and a host, in the same room, connected by a short wire. A host could send messages of up to 8063 bits to its IMP, which would then break these up into packets of at most 1008 bits and forward them independently toward the destination. Each packet was received in its entirety before being forwarded, so the subnet was the first electronic storeand-forward packet-switching network.

##### Original Arpanet Design
![](https://cdn.discordapp.com/attachments/845561994022879264/888847100232732722/unknown.png)

Outside the subnet, software was also needed, namely, the host end of the host-IMP connection, the host-host protocol, and the application software. It soon became clear that BBN was of the opinion that when it had accepted a message on a host-IMP wire and placed it on the host-IMP wire at the destination, its job was done.

### NSFNET 
![](https://cdn.discordapp.com/attachments/845561994022879264/888861422300311613/unknown.png)
NSF also funded some (eventually about 20) regional networks that connected to the backbone to allow users at thousands of universities, research labs, libraries, and museums to access any of the supercomputers and to communicate with one another. The complete network, including backbone and the regional networks, was called NSFNET. 

It connected to the ARPANET through a link between an IMP and a fuzzball in the Carnegie-Mellon machine room. The first NSFNET backbone is illustrated in Fig. 1-28 superimposed on a map of the U.S.

##### Internet Architecture
![](https://cdn.discordapp.com/attachments/845561994022879264/888864989920772146/unknown.png)

The home computer connects to the internet with ISP or Internet Service Provider.
A common way to connect to an ISP is to use the phone line to your house, in which case your phone company is your ISP. DSL, short for Digital Subscriber Line, reuses the telephone line that connects to your house for digital data transmission. The computer is connected to a device called a DSL modem that converts between digital packets and analog signals that can pass unhindered over the telephone line. At the other end, a device called a DSLAM (Digital Subscriber Line Access Multiplexer) converts between signals and packets.

The device at the home end is called a cable modem and the device at the cable headend is called the CMTS (Cable Modem Termination System). The word modem is short for ‘‘modulator demodulator’’ and refers to any device that converts between digital bits and analog signals.

Wireless is used for Internet access too. An example we will explore shortly is that of 3G mobile phone networks. They can provide data delivery at rates of 1 Mbps or higher to mobile phones and fixed subscribers in the coverage area. We can now move packets between the home and the ISP. We call the location at which customer packets enter the ISP network for service the ISP’s POP (Point of Presence). We will next explain how packets are moved between the POPs of different ISPs. From this point on, the system is fully digital and packet switched.

### Third Gen Mobile Phone Networks
First-generation mobile phone systems transmitted voice calls as continuously varying (analog) signals rather than sequences of (digital) bits.

Second-generation mobile phone systems switched to transmitting voice calls in digital form to increase capacity, improve security, and offer text messaging.

The third generation, or 3G, systems were initially deployed in 2001 and offer both digital voice and broadband digital data services. They also come with a lot of jargon and many different standards to choose from.

UMTS (Universal Mobile Telecommunications System), also called WCDMA (Wideband Code Division Multiple Access), is the main 3G system that is being rapidly deployed worldwide. It can provide up to 14 Mbps on the downlink and almost 6 Mbps on the uplink. Future releases will use multiple antennas and radios to provide even greater speeds for users.

The scarce resource in 3G systems, as in 2G and 1G systems before them, is radio spectrum.