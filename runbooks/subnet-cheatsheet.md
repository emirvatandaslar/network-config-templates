# IPv4 subnet cheat sheet / IPv4 alt ağ özeti

| CIDR | Netmask | Addresses | Usable hosts |
|---|---|---|---|
| /32 | 255.255.255.255 | 1 | 1 (single host / loopback) |
| /31 | 255.255.255.254 | 2 | 2 (point-to-point, RFC 3021) |
| /30 | 255.255.255.252 | 4 | 2 |
| /29 | 255.255.255.248 | 8 | 6 |
| /28 | 255.255.255.240 | 16 | 14 |
| /27 | 255.255.255.224 | 32 | 30 |
| /26 | 255.255.255.192 | 64 | 62 |
| /25 | 255.255.255.128 | 128 | 126 |
| /24 | 255.255.255.0 | 256 | 254 |
| /23 | 255.255.254.0 | 512 | 510 |
| /22 | 255.255.252.0 | 1 024 | 1 022 |
| /21 | 255.255.248.0 | 2 048 | 2 046 |
| /20 | 255.255.240.0 | 4 096 | 4 094 |

Usable hosts = 2^(32 − prefix) − 2 (except /31 and /32).
Documentation ranges: `192.0.2.0/24`, `198.51.100.0/24`, `203.0.113.0/24`. Private: `10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`.

Quick check with Python / Python ile hızlı kontrol:

```bash
python -c "import ipaddress as i; n=i.ip_network('203.0.113.0/26'); h=list(n.hosts()); print(n.netmask, n.num_addresses, h[0], h[-1])"
```
