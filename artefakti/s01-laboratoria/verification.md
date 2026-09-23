# Verification

## gw
- Hostname: `gw`
- WAN Internet test: [`ping -c 3 1.1.1.1` succeeded](img/gw_to_internet.png).
- IPv4 forwarding: [`sysctl net.ipv4.ip_forward` returned `1`](img/gw_ip_forwarding.png).
- [Gateway interface addresses](img/gw_ip_table.png) show the configured IPv4 addresses on `gw`.

## srv
- Hostname: `srv`
- LAN1 address: [`192.168.174.2/24`](img/srv_ip_table.png)
- Gateway test: [`ping -c 3 192.168.174.1` succeeded](img/srv_to_gw_connectivity.png).
- [Server LAN1 address](img/srv_ip_table.png) shows `192.168.174.2/24` configured on `srv`.
