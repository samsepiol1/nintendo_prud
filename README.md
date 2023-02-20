<center><h2>Nintendo PRUD</h2></center>
<p align="center"><a href="https://nintendo.com" target="_blank"><img src="https://logodownload.org/wp-content/uploads/2017/04/nintendo-logo-1-1.png" width="400" alt="Nintendo Logo"></a></p>

## About PRUD Protocol

PRUDP is a transport layer protocol on top of UDP whose aim is to reliably and securely send UDP packets. There are two versions of this protocol (V0 and V1), but these are pretty similar. The primary difference lies in the encoding of the packets. All values are encoded in little endian byte order.

On the Nintendo Switch, NEX uses a WebSocket connection instead of UDP and the 'Lite'-encoding is used.


## About udp.h
The "udp.h" header file in BSD systems provides definitions and structures for working with the User Datagram Protocol (UDP) at the transport layer of the Internet Protocol (IP) networking model. It defines the UDP header structure and related constants, such as the UDP port numbers and protocol numbers, as well as the function prototypes for various UDP operations, such as sending and receiving UDP datagrams. The header file also includes macros for handling byte ordering, which is important for ensuring interoperability between different computer architectures that use different byte orders.

```c
#ifndef _NETINET_UDP_H_
#define	_NETINET_UDP_H_

/*
 * UDP protocol header.
 * Per RFC 768, September, 1981.
 */
struct udphdr {
	u_short	uh_sport;		/* source port */
	u_short	uh_dport;		/* destination port */
	u_short	uh_ulen;		/* udp length */
	u_short	uh_sum;			/* udp checksum */
};

/* 
 * User-settable options (used with setsockopt).
 */
#define	UDP_ENCAP			1

/* Start of reserved space for third-party user-settable options. */
#define	UDP_VENDOR			SO_VENDOR

/*
 * UDP Encapsulation of IPsec Packets options.
 */
/* Encapsulation types. */
#define	UDP_ENCAP_ESPINUDP_NON_IKE	1 /* draft-ietf-ipsec-nat-t-ike-00/01 */
#define	UDP_ENCAP_ESPINUDP		2 /* draft-ietf-ipsec-udp-encaps-02+ */

/* Default ESP in UDP encapsulation port. */
#define	UDP_ENCAP_ESPINUDP_PORT		500

/* Maximum UDP fragment size for ESP over UDP. */
#define	UDP_ENCAP_ESPINUDP_MAXFRAGLEN	552

#endif
```
