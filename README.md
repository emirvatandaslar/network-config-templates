# network-config-templates

Copy-paste-ready, commented **Juniper Junos** and **Cisco IOS** configuration templates plus short troubleshooting runbooks for everyday data-center networking.

Günlük veri merkezi ağ işleri için yorumlu **Juniper Junos** ve **Cisco IOS** şablonları ve kısa sorun giderme rehberleri.

> ⚠️ All ASNs, IPs and names are documentation placeholders (RFC 5398 / RFC 5737). Review every line before applying; use `commit confirmed` on Junos and `reload in` on IOS when changing remote devices.
>
> Tüm ASN/IP/isimler örnektir. Uygulamadan önce her satırı gözden geçirin; uzak cihazlarda Junos'ta `commit confirmed`, IOS'ta `reload in` kullanın.

| Path | Content |
|---|---|
| [`juniper/bgp-ebgp-upstream.set`](juniper/bgp-ebgp-upstream.set) | eBGP to an upstream with import/export filtering |
| [`juniper/vlan-irb-access-trunk.set`](juniper/vlan-irb-access-trunk.set) | VLANs, IRB gateways, access & trunk ports |
| [`juniper/lacp-aggregated-ethernet.set`](juniper/lacp-aggregated-ethernet.set) | LACP aggregated Ethernet (ae0) |
| [`juniper/re-protection-filter.set`](juniper/re-protection-filter.set) | Routing-engine (lo0) protection filter |
| [`cisco/vlan-trunk-lacp.ios`](cisco/vlan-trunk-lacp.ios) | VLAN, SVI, access/trunk, LACP port-channel |
| [`cisco/bgp-ospf-basic.ios`](cisco/bgp-ospf-basic.ios) | eBGP with prefix lists + OSPF |
| [`runbooks/bgp-session-troubleshooting.md`](runbooks/bgp-session-troubleshooting.md) | BGP state → cause, Junos vs IOS commands |
| [`runbooks/packet-loss-triage.md`](runbooks/packet-loss-triage.md) | Systematic loss/latency triage |
| [`runbooks/subnet-cheatsheet.md`](runbooks/subnet-cheatsheet.md) | CIDR table and quick checks |

Templates were written from vendor documentation conventions and have not been run against production devices from this repository; always test in a lab first.

MIT licensed.
