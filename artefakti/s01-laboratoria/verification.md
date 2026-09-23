# Verification

## gw
- Hostname: `gw`
- WAN Internet test: `ping -c 3 1.1.1.1` succeeded.

	![Gateway WAN Internet test](img/gw_to_internet.png)
- IPv4 forwarding: `sysctl net.ipv4.ip_forward` returned `1`.

	![Gateway IPv4 forwarding](img/gw_ip_forwarding.png)
- Gateway interface addresses show the configured IPv4 addresses on `gw`.

	![Gateway interface addresses](img/gw_ip_table.png)

## srv
- Hostname: `srv`
- LAN1 address: `192.168.174.2/24`

	![Server LAN1 address](img/srv_ip_table.png)
- Gateway test: `ping -c 3 192.168.174.1` succeeded.

	![Server-to-gateway connectivity](img/srv_to_gw_connectivity.png)
