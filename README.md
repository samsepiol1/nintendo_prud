<center><h2>Nintendo PRUDP</h2></center>
<p align="center"><a href="https://nintendo.com" target="_blank"><img src="https://logodownload.org/wp-content/uploads/2017/04/nintendo-logo-1-1.png" width="400" alt="Nintendo Logo"></a></p>

## About PRUDP Protocol

PRUDP is a transport layer protocol on top of UDP whose aim is to reliably and securely send UDP packets. There are two versions of this protocol (V0 and V1), but these are pretty similar. The primary difference lies in the encoding of the packets. All values are encoded in little endian byte order.

On the Nintendo Switch, NEX uses a WebSocket connection instead of UDP and the 'Lite'-encoding is used.

## PRUDP Session

```hex
Handshake 1   → af a1 40 00 00 00 00 00 00 00 00 00 00 00 00 97

Handshake 1   ← a1 af 10 00 00 00 00 00 00 00 00 5f 22 68 ea 3a

Handshake 2   → af a1 61 00 18 5f 22 68 ea 01 00 d4 d6 91 e8 c9

Handshake 2   ← a1 af 11 00 50 d4 d6 91 e8 01 00 00 00 00 00 de

Send data     → af a1 62 00 18 26 b4 01 a1 02 00 00 (25 bytes of encrypted payload) ef

Acknowledge   ← a1 af 12 00 50 78 56 34 12 02 00 00 d1

Send data     ← a1 af 62 00 50 67 dd f9 c3 01 00 00 (255 bytes of encrypted payload) 03

Acknowledge   → af a1 12 00 18 78 56 34 12 01 00 00 97

Send data     → af a1 62 00 18 8d 58 91 c0 03 00 00 (21 bytes of encrypted payload) fa

Acknowledge   ← a1 af 12 00 50 78 56 34 12 03 00 00 d2

Send data     ← a1 af 62 00 50 a9 c5 fa 2e 02 00 00 (130 bytes of encrypted payload) 54

Acknowledge   → af a1 12 00 18 78 56 34 12 02 00 00 98

Hangup        → af a1 63 00 18 5f 22 68 ea 04 00 aa

Hangup        ← a1 af 13 00 50 d4 d6 91 e8 04 00 e2
```

## PRUDP Packet Structure

| Offset | Description |
|------|-----------|
| 0x0 |   Source     |
| 0x1|   Destination |
| 0x2 |  Type and Flags    |
| 0x4 |  Session ID    |
| 0x5 |  Packet signature    |
| 0x9 |  Sequence ID     |



## About udp.h
The "udp.h" header file in BSD systems provides definitions and structures for working with the User Datagram Protocol (UDP) at the transport layer of the Internet Protocol (IP) networking model. It defines the UDP header structure and related constants, such as the UDP port numbers and protocol numbers, as well as the function prototypes for various UDP operations, such as sending and receiving UDP datagrams. The header file also includes macros for handling byte ordering, which is important for ensuring interoperability between different computer architectures that use different byte orders.

This struct can be used to access the different fields of a UDP header in a C program

```c
struct udphdr {
	u_short	uh_sport;		/* source port */
	u_short	uh_dport;		/* destination port */
	u_short	uh_ulen;		/* udp length */
	u_short	uh_sum;			/* udp checksum */
};

```

The struct contains four fields:

1. "uh_sport" is a 16-bit unsigned integer that represents the source port number of the UDP packet.

2 ."uh_dport" is a 16-bit unsigned integer that represents the destination port number of the UDP packet.

3. "uh_ulen" is a 16-bit unsigned integer that represents the length of the UDP packet (including the header and data).

4 . "uh_sum" is a 16-bit unsigned integer that represents the checksum of the UDP packet.

## PRUPD Header in C

This code is defining a C language structure named prudphdr, which represents the header of the PRUDP (Nintendo's Reliable Datagram Protocol) packet. The structure contains the 

```c

struct prudphdr {

    uint16_t uh_sport;		/* source port rewrite (C 99 ) */
    uint16_t uh_dport;		/* destination port */
    uint16_t uh_ulen;		/* pruudp length */
    uint8_t  uh_sum;			/* prudp checksum rewrite to 8 bits */
    uint8_t uh_type;        /* prudp type msg */
    uint16_t uh_seq_num;    /* prudp seq number packet */
    uint16_t uh_session_id;     /* identificador de sessão */
    uint32_t uh_timestamp;   
    uint16_t uh_payload_size;   /* tamanho do payload do pacote de dados */

};
```

