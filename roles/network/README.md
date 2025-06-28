# Ansible Role: network

This role configure the basic networking functionality of a linux distro

## Role Variables

- `network_wifi_ssid` the name of the WIFI network to be configured (default: "").
- `network_wifi_pass` the passphrase of the WIFI network to be configure (default: "").

## Internals

### Archlinux

- ensure that `dhcpcd` and `networkmanager` packages are installed
- configure `NetworkManager` connectivity, dhcp client, captive portal functionality,
MAC address randomization, ipv6 privacy, and default network connection (if provided).
