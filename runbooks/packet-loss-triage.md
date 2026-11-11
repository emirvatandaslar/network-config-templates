# Packet loss / latency triage / Paket kaybı ve gecikme analizi

## 🇬🇧 English

1. **Scope it** – one customer, one destination, one direction, or everyone? Get source IP, destination IP and time window.
2. **Reproduce from both ends** – `mtr -rwzc 100 <dst>` from the server **and** a reverse `mtr` from the destination. Real loss shows **on the hop and on every hop after it**; loss on a single hop only is usually ICMP rate-limiting.
3. **Check our edge** – interface errors/discards (`show interfaces extensive`: input/output errors, CRC, drops), LACP member balance, utilization against port speed.
4. **Check the control plane** – BGP flaps in the log (`show log messages | match BGP`), best-path changes, a sudden new upstream.
5. **Check for an attack** – a pps/Mbps spike on monitoring (PRTG/FastNetMon) coinciding with the loss → follow the DDoS runbook.
6. **Check MTU** – `ping -M do -s 1472 <dst>` (Linux). Failure at 1472 but success at smaller sizes indicates a path MTU problem.
7. **Escalate with evidence** – hop-by-hop `mtr` from both directions, UTC timestamps, affected prefixes.

## 🇹🇷 Türkçe

1. **Kapsamı belirleyin** – tek müşteri mi, tek hedef mi, tek yön mü, herkes mi? Kaynak/hedef IP ve zaman aralığını alın.
2. **İki uçtan test edin** – sunucudan `mtr -rwzc 100 <hedef>` ve hedeften geri yönde `mtr`. Gerçek kayıp o hopta **ve sonraki tüm hoplarda** görünür; yalnız tek hopta görünen kayıp çoğunlukla ICMP sınırlamasıdır.
3. **Kendi kenar cihazınıza bakın** – arayüz hataları/drop (CRC, input/output errors), LACP üye dengesi, port kullanımı.
4. **Kontrol düzlemi** – log'da BGP kopmaları, best-path değişimi.
5. **Saldırı var mı?** – izlemede pps/Mbps artışı kayıpla çakışıyorsa DDoS runbook'una geçin.
6. **MTU** – `ping -M do -s 1472 <hedef>`; 1472'de hata, küçüklerde yok ise yol MTU sorunu vardır.
7. **Kanıtla yükseltin** – iki yönlü `mtr`, UTC zaman damgaları, etkilenen prefix'ler.
