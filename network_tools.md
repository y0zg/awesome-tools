# Network Tools and Resources

A collection of networking tools, concepts, and references

## IP Management Tools

- [ipcalc](https://jodies.de/ipcalc) - IP address subnet calculator
- [Network00](https://network00.com/) - Network planner and subnet calculator
- [IP Calculator](https://jodies.de/ipcalc) - Interactive IP addressing utility
- [PHPIPAM](https://phpipam.net/) - IP address management system

## DNS Tools

- [dig](https://linux.die.net/man/1/dig) - DNS lookup utility
- [nslookup](https://linux.die.net/man/1/nslookup) - Query DNS name servers
- [host](https://linux.die.net/man/1/host) - DNS lookup utility
- [whois](https://linux.die.net/man/1/whois) - Query WHOIS servers

## Network Analysis

- [Wireshark](https://www.wireshark.org/) - Network protocol analyzer
- [tcpdump](https://www.tcpdump.org/) - Command-line packet analyzer
- [nmap](https://nmap.org/) - Network discovery and security auditing
- [mtr](https://github.com/traviscross/mtr) - Network diagnostic tool

## VPN Solutions

- [OpenVPN](https://openvpn.net/) - Open source VPN solution
- [WireGuard](https://www.wireguard.com/) - Simple, fast, modern VPN
- [IPsec](https://tools.ietf.org/html/rfc6071) - Internet Protocol Security

## Network Concepts

### Traffic Patterns

- **East-West Traffic**: Server-to-server communication within a data center (horizontal)
- **North-South Traffic**: Client-to-server traffic between data center and external networks (vertical)

### Addressing Methods

- **Unicast**: One-to-one communication
- **Broadcast**: One-to-all communication
- **Multicast**: One-to-many-of-many communication
- **Anycast**: One-to-nearest communication
- **Geocast**: Delivery to geographical group

### Network Security

#### IPSec Phases

- **Phase 1**: Creates secure channel using diffie-hellman key exchange
- **Phase 2**: Establishes IPSec security associations for tunneling

#### NAT Types

- **Static NAT**: One-to-one mapping of private to public addresses
- **Dynamic NAT**: Many-to-many mapping from pool of addresses
- **PAT (Overloaded NAT)**: Many-to-one mapping using different ports

## Advanced Networking Concepts

- **Link Aggregation Control Protocol (LACP)**: Manages multiple physical ports as single channel
- **Jumbo Frames**: Ethernet frames with more than 1500 bytes payload (up to 9000)
- **Ephemeral Ports**: Temporary ports used for client connections
  - Linux: 32768-61000
  - FreeBSD: 1024-5000 (older), IANA range (newer)
  - Windows: Custom range within 1025-65535
  - AWS ELB: 1024-65535

## Cloud Networking

- [AWS IP Ranges](https://ip-ranges.amazonaws.com/ip-ranges.json) - Official AWS IP address ranges
- [VPC Designer](https://vpcdesigner.com/) - Visual AWS VPC design tool
- [Azure Network Watcher](https://azure.microsoft.com/en-us/services/network-watcher/) - Network performance monitoring

## References

- [FIPS Codes by Region](https://transition.fcc.gov/oet/info/maps/census/fips/fips.txt) - Federal Information Processing Standards codes
- [Private Domain RFC](https://www.rfc-editor.org/rfc/rfc6762#appendix-G) - Standards for private domains 