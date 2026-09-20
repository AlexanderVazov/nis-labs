# Verification

## gw
- Hostname: `gw`
- WAN Internet test: `ping -c 3 1.1.1.1` succeeded.
- IPv4 forwarding: `sysctl net.ipv4.ip_forward` returned `1`.

## srv
- Hostname: `srv`
- LAN1 address: `192.168.10.10/24`
- Gateway test: `ping -c 3 192.168.10.1` succeeded.
