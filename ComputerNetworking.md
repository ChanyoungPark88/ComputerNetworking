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

| 5   | Application | HTTP,SMTP,etc..   | Messages | n/a         |
| --- | ----------- | ----------------- | -------- | ----------- |
| 4   | Transport   | TCP/UDP           | Segment  | Port #'s    |
| --- | ----------- | ----------------- | -------- | ----------- |
| 3   | Network     | IP                | Datagram | IP address  |
| --- | ----------- | ----------------- | -------- | ----------- |
| 2   | Data Link   | Ethernet, Wi-Fi   | Frames   | MAC Address |
| --- | ----------- | ----------------- | -------- | ----------- |
| 1   | Physical    | 10 Base T, 802.11 | Bits     | n/a         |

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

Thus, Hub is layer 1 device, Switch is layer 2 device, Router is layer 3 device. A network which connected to hub is a segment called Collision domain. In Collision Domain, only one device can communicate at a time, if one device communicate, other devices can not communicate. Switch has memory to store Mac address of each devices in network. Hub and Switch are working on Local Area Network whereas Router is device to forward data to between independent networks. Router has routing tables. Router gets data inside network, and forward it to ISP(=Internet Service Provider)
