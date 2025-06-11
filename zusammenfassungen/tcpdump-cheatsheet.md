# 📄 tcpdump Cheatsheet

tcpdump ist ein CLI-Tool zum Live-Mitschnitt oder zur Analyse von Netzwerkverkehr. Nützlich in Pentests, Forensik, Incident Response oder zur schnellen Fehlersuche.

---

## 🔧 Grundlagen

tcpdump -i eth0              # Pakete auf Interface eth0 beobachten

tcpdump -n                   # Keine DNS-Namen auflösen (nur IPs)

tcpdump -nn                  # Auch keine Portnamen auflösen (nur Nummern)

tcpdump -c 100               # Nach 100 Paketen stoppen

tcpdump -w traffic.pcap      # Mitschnitt speichern (für Wireshark)

tcpdump -r traffic.pcap      # Mitschnitt analysieren


# Filterbeispiele

tcpdump host 192.168.1.10             # Ein Host (egal ob Quelle oder Ziel)

tcpdump src host 10.0.0.1             # Nur Pakete VON 10.0.0.1

tcpdump dst host 10.0.0.1             # Nur Pakete AN 10.0.0.1

tcpdump port 80                       # Pakete über Port 80

tcpdump tcp port 443                  # Nur TCP über Port 443

tcpdump udp                           # Nur UDP-Pakete

tcpdump src net 192.168.0.0/24        # Quelle aus ganzem Subnetz

tcpdump '(src net 10.0.0.0/24) and (dst port 80 or 443)'  
# Nur Web-Ziele aus Subnetz – guter Filter bei Incident Response

# Protokollanalyse
tcpdump tcp                             # Nur TCP

tcpdump udp                             # Nur UDP

tcpdump icmp                            # Nur ICMP (Ping etc.)

tcpdump arp                             # ARP-Traffic sichtbar machen

tcpdump ether                           # Ethernet-Header anzeigen

tcpdump -e                              # Zeigt auch MAC-Adressen


💡 -s 0 bedeutet: Max. Snaplen = vollständiger Paketinhalt

tcpdump -A -s 0 -i eth0 port 80
# ASCII-Inhalte auf HTTP-Port anzeigen (z. B. Passwörter)

tcpdump -X -s 0 -i eth0 port 80
# Hex + ASCII-Dump aller HTTP-Daten

tcpdump 'tcp[tcpflags] & tcp-syn != 0'
# Nur SYN-Pakete (Verbindungsversuche) – gut für Portscan-Erkennung

tcpdump 'tcp[tcpflags] & (tcp-syn|tcp-ack) == (tcp-syn|tcp-ack)'
# Nur SYN/ACK – zeigt, welche Ports offen sind (z. B. nach einem Scan)

tcpdump 'tcp port 21 and (((ip[2:2] - ((ip[0]&0xf)<<2)) - ((tcp[12]&0xf0)>>2)) != 0)'
# Nur FTP-Datenkanal – Steuerkanal wird ignoriert

tcpdump 'tcp dst port 22 and src net 192.168.1.0/24'
# SSH-Zugriffe aus lokalem Netz sichtbar machen

tcpdump 'udp port 53'
# DNS-Anfragen sichtbar machen

tcpdump -i eth0 port not 22
# Alles außer SSH anzeigen – nützlich, wenn du via SSH verbunden bist

tcpdump 'port 443 and tcp[13] == 18'
# TCP-Pakete mit PSH+ACK – zeigt oft Nutzdaten

tcpdump 'icmp[icmptype] == 8'
# ICMP Echo Request (Ping)


tcpdump -i eth0 -l | tee live.log
# -l (line-buffered) + tee erlaubt Live-Analyse & Mitschnitt zugleich: