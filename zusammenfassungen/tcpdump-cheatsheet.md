# 📄 tcpdump Cheatsheet

> `tcpdump` ist ein leistungsfähiges CLI-Tool zur Analyse und Filterung von Netzwerkpaketen in Echtzeit oder aus Mitschnitten, ideal für Pentesting, Forensik und Netzwerkdiagnose.

---

## 🔧 Grundlagen

tcpdump -i eth0 -q

tcpdump ip

tcpdump host 192.168.1.10

tcpdump tcp
tcpdump udp

tcpdump port 80

tcpdump src host 10.0.0.1
tcpdump dst host 10.0.0.1

tcpdump tcp port 443

tcpdump -i eth0 -w dump.pcap
tcpdump -r dump.pcap

tcpdump -n
# Anzeige ohne DNS-Auflösung (nur IPs, keine Hostnamen)

tcpdump 'tcp[tcpflags] & tcp-syn != 0'
# Zeigt nur SYN-Pakete – nützlich zur Erkennung von Verbindungsversuchen

tcpdump '(src net 10.0.0.0/24) and (dst port 80 or 443)'
# Nur ausgehender Traffic aus Subnetz zu Webservern (HTTP/HTTPS)

tcpdump -A -s 0 -i eth0 port 80
# Zeigt HTTP-Inhalte (ASCII) live gut für einfache Webforensik

tcpdump 'tcp port 21 and (((ip[2:2] - ((ip[0]&0xf)<<2)) - ((tcp[12]&0xf0)>>2)) != 0)'
# Nur FTP-Datenverkehr anzeigen (kein Steuerkanal)

ip[2:2]                          → Gesamte Paketgröße
- ((ip[0]&0xf)<<2)              → Abzüglich IP-Header
- ((tcp[12]&0xf0)>>2)           → Abzüglich TCP-Header
= 🧩 verbleibende Payloadgröße

-e 
# MAC
