# BGP session troubleshooting / BGP oturumu sorun giderme

## 🇬🇧 English

Work bottom-up: **L1/L2 → L3 reachability → TCP/179 → BGP state → policy**.

| Step | Junos | Cisco IOS |
|---|---|---|
| Link up? | `show interfaces <if> terse` / `extensive` | `show interfaces <if>` |
| Peer reachable? | `ping <peer> source <our-ip> rapid count 20` | `ping <peer> source <our-ip> repeat 20` |
| TCP/179 reaching the router? | `show firewall filter PROTECT-RE` (counters) | `show access-lists` |
| Session state | `show bgp summary` / `show bgp neighbor <peer>` | `show ip bgp summary` / `show ip bgp neighbors <peer>` |
| What we advertise | `show route advertising-protocol bgp <peer>` | `show ip bgp neighbors <peer> advertised-routes` |
| What we receive | `show route receive-protocol bgp <peer>` | `show ip bgp neighbors <peer> routes` |
| Why a route is hidden | `show route hidden extensive` | `show ip bgp <prefix>` |

State → likely cause:

- **Idle** – no route to the peer, peer administratively down, or prefix-limit teardown (clear after fixing).
- **Active / Connect** – TCP is not completing: ACL/firewall filter, wrong peer IP, MTU or asymmetric routing.
- **OpenSent / OpenConfirm loop** – wrong `peer-as`, authentication key mismatch, capability mismatch.
- **Established but no routes** – import policy rejecting, or the peer is not announcing (check its export policy).

## 🇹🇷 Türkçe

Alttan yukarı ilerleyin: **L1/L2 → L3 erişim → TCP/179 → BGP durumu → politika**. Yukarıdaki tablodaki komutlarla sırayla bakın.

- **Idle** – komşuya rota yok, komşu kapalı ya da prefix-limit nedeniyle oturum kapandı.
- **Active / Connect** – TCP kurulamıyor: ACL/firewall filtresi, yanlış IP, MTU ya da asimetrik yönlendirme.
- **OpenSent / OpenConfirm döngüsü** – `peer-as` yanlış, kimlik doğrulama anahtarı uyuşmuyor.
- **Established ama rota yok** – import politikası reddediyor ya da karşı taraf duyurmuyor.
