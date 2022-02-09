1. Introduction to Computer Networking

- Protocol: a defined set of standards that computers must follow in order to communicate properly
- Computer networking: full scope of how computers communicate with each other

2. TCP/IP 5 Layer model

- Physical(L1) : Represent the physical devices that interconnect computers (e.g. Network cable)
- Data Link(L2) : Responsible for defining a common way of interpreting these signals so network devices can communicate (e.g. Ethernet, Wi-fi)
  - The **Ehternet** standards also define a protocol resposible for getting data to nodes on the same network or link
- Network(L3) : Allows different networks to communicate with each other through devices known as routers (e.g. IP)
  - Internetwork: A collection of networks connected together through routers, the most famous of these being the **Internet**
  - IP(Internet Protocol): **IP** is the heart of the internet and most smaller networks around the world
- Transport(L4) : Sorts out which client and server programs are supposed to get that data (e.g. TCP(=Transmission Control Protocol) /UDP(=User Datagram Protocol))
  - The big differnce between the two is that TCP provides mechanisms to ensure that data is reliably delivered while UDP does not.
- Application(L5) :

```
| #   | Layer Name  | Protocol          | Protocol Data Unit | Addressing  |
| --- | ----------- | ----------------- | ------------------ | ----------- |
| 5   | Application | HTTP,SMTP,etc..   | Messages           | n/a         |
| --- | ----------- | ----------------- | ------------------ | ----------- |
| 4   | Transport   | TCP/UDP           | Segment            | Port #'s    |
| --- | ----------- | ----------------- | ------------------ | ----------- |
| 3   | Network     | IP                | Datagram           | IP address  |
| --- | ----------- | ----------------- | ------------------ | ----------- |
| 2   | Data Link   | Ethernet, Wi-Fi   | Frames             | MAC Address |
| --- | ----------- | ----------------- | ------------------ | ----------- |
| 1   | Physical    | 10 Base T, 802.11 | Bits               | n/a         |
```

3. The Basic of Networking Devices

- Cables

  - To connect different devices to each other
  - Most two categories are copper and fiber
  - Copper cables are most common form
  - Most uses are Cat 5, Cat 5e, Cat 6
  - Cat 5 have a problem called crosstalk so it replaced older Cat 5. \*Crosstalk is when an electrical pulse on one wire is accidentally detected on another wire.
  - Fiber cables can generally transport data quicker than copper cables can, but they're much more expensive and fragile
  - Fiber can also transport data over much longer distances than copper can without suffering potential data loss

- Hub

  - **A physical layer device** that allows for connections from many computers at once.
  - Each system connected to hub, it called collision domain
  - Collision domain is a network segment where only one device can communicate at a time.

- Network Switch(A.K.A Switching hub)

  - Role is similar to hub
  - **The difference is that while a hub is a layer one or physical layer device, a switch is a layer two or data link device.**

- Router
  - Operates at 3rd layer(=Network)

```
Thus, Hub is layer 1 device, Switch is layer 2 device, Router is layer 3 device. A network which connected to hub is a segment called Collision domain. In Collision Domain, only one device can communicate at a time, if one device communicate, other devices can not communicate. Switch has memory to store Mac address of each devices in network. Hub and Switch are working on Local Area Network whereas Router is device to forward data to between independent networks. Router has routing tables. Router gets data inside network, and forward it to ISP(=Internet Service Provider)
```

4. The Physical Layer

- consist of devices and transmmiting bits across computer networks

  - Bit: The smallest representation of data (that a computer can understand.) 1 or 0
  - Modulation: A way of varying the voltage of this charge moving across the cable
  - Line coding: It's a specific kind of modulation. In telecommunication, a line code is a pattern of voltage, current, or photons used to represent digital data transmitted down a transmission line. by Wikipedia

- Twisted pair cabling: twisted nature helps protect against electromagnetic interference and crosstalk from neighboring pairs. In all modern forms of networking, **it's important to know that these cables allow for duplex communication**

  - Duplex communication: The concept that information can flow in both directions across the cable
  - Simplex communcation: This process is unidirectional
  - Half duplex communication:

5. The Data Link Layer

- Ethernet: As a protocol solved problem in collision domain by using a technique known as carrier sense multiple access with collision detection.

- CSMA/CD: Used to determine when the communications channels are clear and when the device is free to transmit data.

- MAC(Media Access Control) Address: A globally unique identifier attached to an individual network interface. It's a 48-bit number normally represented by six groupings of two hexadecimal numbers.
  - Hexadecimal: A way to represent numbers using 16 digits
  - Octet: In computer networking, any number that can be represented by 8 bits

```
| Hexadecimal | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | A   | B   | C   | D   | E   | F   |
| ----------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Decimal     | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  | 11  | 12  | 13  | 14  | 15  |
```

- MAC Address is split into two sections

  - OUI(Organizationally Unique Identifier): The first three octets of a MAC Address
  - Vendor Assigned: last three octets

- Unicast: One on one communication. always meant for just one receiving address
- Multicast: A multicast frame is similarly set to all devices on the local network signal.
- Broadcast: An Ethernet broadcast is sent to every single device on a LAN.

- Dissecting an Ethernet Frame
  - Data packet: An all-encompassing term that represents any single set of binary data being sent across a network link.

```
| Preamble | SFD | Destination address | Source address | VLAN header | Ether-type | Payload | FCS |
| -------- | --- | ------------------- | -------------- | ----------- | ---------- | ------- | --- |
```

    - Preamble: Bits that representing where start frame (8 bytes)
      - SFD(start frame delimiter): Last one byte in preamble (1 byte)
    - Destination address: Physical address that network adaptor of the recipient (6 bytes)
    - Source address: Physical address that network adaptor of the sender (6 bytes)
    - (optional) VLAN header: It designed that lots of Vlan works on the same network switch (4 bytes)
    - Ehter-type: Representing size of data field (2 bytes)
    - Payload: All higher lever data included (0 - 1,500 bytes)
    - FCS(Frame Check Sequence): Checksum (4 bytes)
      - Checksum: It is a feature to find error. This checksum value is calculated by performing what's known as a cyclical redundancy check against the frame
      - CRC(Cyclical Redundancy Check): Basically a mathematical transformation that uses polynomial division to create a number that represents a larger set of data. Anytime you perform a CRC against a set of data, you should end up with the same checksum number. The reason it's included in the Ethernet frame is so that the receiving network interface can infer if it received uncorrupted data.
