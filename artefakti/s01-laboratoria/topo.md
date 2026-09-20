# S01 laboratory topology

The lab contains two Fedora minimal virtual machines, managed with KVM/libvirt
through Virtual Machine Manager.

| VM | Resources | Network interfaces | IPv4 configuration |
|---|---:|---|---|
| `gw` | 1 vCPU, 1 GiB RAM | WAN, LAN1, LAN2 | WAN: DHCP (libvirt default NAT); LAN1: `192.168.10.1/24`; LAN2: `192.168.20.1/24` |
| `srv` | 2 vCPUs, 4 GiB RAM | LAN1 | `192.168.10.10/24`, gateway `192.168.10.1` |

```text
                       Internet
                          |
              WAN: libvirt "default" (NAT/DHCP)
                          |
                    [ gw / Fedora ]
                  1 vCPU, 1 GiB RAM
          LAN1 192.168.10.1/24 | LAN2 192.168.20.1/24
                 |             |
        [ srv / Fedora ]       +-- isolated LAN2 (reserved for later hosts)
      2 vCPUs, 4 GiB RAM
        192.168.10.10/24
```

`LAN1` and `LAN2` are isolated libvirt networks with DHCP disabled. The WAN
uses libvirt's standard `default` network, which supplies an address by DHCP
and NATs outbound traffic. IPv4 forwarding is enabled persistently on `gw`.
