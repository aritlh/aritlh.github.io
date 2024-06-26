---
title: 'Network Security #3 Data Encapsulation'
date: 2024-04-16 12:57:13
---

Each layer in the IPS is built on the one below, and each layer is able to encapsulate the data from the layer above so it can move between the layers. Data transmitted by each layer is called a protocol data unit (PDU).

## Headers, Footers, and Addresses
The PDU in each layer contains the payload data that is being transmitted. It's commont to prefix a header--which contains information required for the payload data to be transmitted, such as the addresses of the source and destination nodes on the network--to the payload data. Sometimes a PDU also has a footer that is suffixed to the payload data and contains values needed to ensure correct transmission, such as error-checking information. Figure below shows how the PDUs are laid out in the IPS.

![IPS Data Encapsulation](https://i.imgur.com/umgtap6.png)

The TCP header contains a source destination port number ➊. These port numbers allow a single node to have multiple unique network connections. Port numbers for TCP (and UDP) range from <ins>0 to 65535</ins>. Most port numbers are assigned as needed to new connections, but some numbers have been given special assignments, such as poort 80 for HTTP. (You can find a current list of assigned port numbers in the `/etc/services` file on most Unix-like OS.) A TCP payload and header are commonly called segment, whereas a UDP payload and header are commonly called a datagram.

The IP protocol uses a source and a destination address ➋. The destination address allows the data to be sent to a specific node on the network. The source address allows the receiver of the data to know which node sent the data and allows the receiver to reply to the sender.

IPv4 uses 32-bit addresses, which you'll typically ssee written as four number separated by dots, such as 192.168.10.1. IPv6 uses 128-bit addresses, because 32-bit addresses aren't sufficient for the number of nodes on modern networks. IPv6 addresses are usually written as hexadecimal numbers separated by colons, such as fe80:0000:0000:0000:897b:581e:44b0:2057. Long strings of 0000 numbers are collapsed into two colons. For example, the preceding IPv6 address can also be written as fe80::897b:581e:44b0:2057. An IP payload and header are commonly called a packet.

Ethernet also contains source and destination addresses ➌. Ethernet uses a 64-bit value called a Media Access Control (MAC) address, which is typically set during manufacture of the Ethernet adapter. You’ll usually see MAC addresses written as a series of hexadecimal numbers separated by dashes or colons, such as 0A-00-27-00-00-0E. The Ethernet payload, including the header and footer, is commonly referred to as a frame.