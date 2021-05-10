# Gateway-to-gateway (site-to-site) L2TP/IPsec tunnel with null encryption
Security achieved via internal certs.
Included in the repo are `swanctl` config files, private keys, certs, `xl2tpd` config files, `pppd` config files and a packet capture of a communication between the two subnets in cleartext (a single ICMP exchange)

If it's not clear from the title, encryption and authentication are NULL for educational purposes, with minimal ciphers used as required to enable communications between the two endpoints.

IPsec is in tunnel mode.

## Test topology
```
                10.10.1.0/30          20.20.1.0/30
                        ─┬─           ─┬─
                ┌────┐   │             │  ┌────────┐
                │    │.1 │             │.1│        │
                │ GW ├───┴──── WAN ────┴──┤ SERVER │
                │    │32.32.1.2  32.32.1.1│        │
                └──┬─┘      \      /      └───┬────┘
               │ .1│          L2TP            │.1   │
 192.168.1.0/24├───┤         TUNNEL           ├─────┤192.168.2.0/24
               │ .2│                          │.2   │
                ┌──┴─┐                      ┌─┴──┐
                │    │                      │    │
                │ H1 │                      │ H2 │
                │    │                      │    │
                └────┘                      └────┘
```
