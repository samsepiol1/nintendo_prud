<center><h2>Nintendo PRUD</h2></center>
<p align="center"><a href="https://nintendo.com" target="_blank"><img src="https://logodownload.org/wp-content/uploads/2017/04/nintendo-logo-1-1.png" width="400" alt="Nintendo Logo"></a></p>

## About PRUD Protocol

PRUDP is a transport layer protocol on top of UDP whose aim is to reliably and securely send UDP packets. There are two versions of this protocol (V0 and V1), but these are pretty similar. The primary difference lies in the encoding of the packets. All values are encoded in little endian byte order.

On the Nintendo Switch, NEX uses a WebSocket connection instead of UDP and the 'Lite'-encoding is used.


## About udp.h
The "udp.h" header file in BSD systems provides definitions and structures for working with the User Datagram Protocol (UDP) at the transport layer of the Internet Protocol (IP) networking model. It defines the UDP header structure and related constants, such as the UDP port numbers and protocol numbers, as well as the function prototypes for various UDP operations, such as sending and receiving UDP datagrams. The header file also includes macros for handling byte ordering, which is important for ensuring interoperability between different computer architectures that use different byte orders.
```c
printf("aqui vai algo");
```
