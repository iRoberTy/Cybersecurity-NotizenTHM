# 🌐 Netzwerk-Zusammenfassung

## 1. Was ist ein Netzwerk?
Ein Netzwerk ist ein Verbund von Geräten (Clients, Servern, Routern), die über physikalische oder drahtlose Medien Daten austauschen.
Ziel: Ressourcen teilen, Kommunikation ermöglichen, Dienste nutzen.

🔎 Typen: LAN, WAN, WLAN, VPN, MAN, PAN
---

## 2. Wichtige Begriffe
 _______________________________________________________
|  Begriff  |                 Erklärung                 |
|-----------|-------------------------------------------|
|IP-Adresse |Eindeutige Adresse eines Geräts im Netzwerk|
|MAC-Adresse|        Physische Hardware-Adresse         |
|   Port    |Virtuelle Schnittstelle für Netzwerkdienste|
| Protokoll |       Regeln für Datenübertragung         |
|  Subnetz  |        Teilbereich eines Netzwerks        |
|  Gateway  |      Vermittler zwischen Netzwerken       |
|    DNS    |Domain Name System – löst Namen in IPs auf |
|   DHCP    |	   Dynamische IP-Vergabe im Netz        |
|    NAT    |Mehr Geräte teilen sich eine öffentliche IP|
|   VLAN    |Virtuelle Netzwerksegmentierung auf Layer 2|

---

## 3. OSI-Modell (7 Schichten)
 _____________________________________________________________________________________
|Schicht: | Name           | Funktion                           | Beispielprotokolle  |
| ------  | -------------- | ---------------------------------- | ------------------- |
|       7 | Anwendung      | Benutzernahe Dienste               | HTTP, FTP, SSH, DNS |
|       6 | Darstellung    | Datenformatierung, Verschlüsselung | TLS/SSL, JPEG       |
|       5 | Sitzung        | Verbindungsmanagement              | NetBIOS, RPC        |
|       4 | Transport      | Zuverlässiger Datenversand         | TCP, UDP            |
|       3 | Netzwerk       | Routing & IP-Adressierung          | IP, ICMP            |
|       2 | Sicherung      | MAC-Adressen, Fehlererkennung      | Ethernet, ARP       |
|       1 | Bitübertragung | Rohdatenübertragung                | Kabel, WLAN, Hubs   |


---

## 4. TCP vs. UDP
 ________________________________________________________________________________
| Kriterium       | TCP                            | UDP                         |
| --------------- | ------------------------------ | --------------------------- |
| Verbindung      | Verbindungsorientiert          | Verbindungslos              |
| Zuverlässigkeit | Bestätigt Empfang, Reihenfolge | Keine Garantie              |
| Geschwindigkeit | Langsamer (Overhead)           | Schneller (leichtgewichtig) |
| Anwendungen     | HTTP, SSH, FTP, SMTP           | DNS, VoIP, NTP, TFTP        |


---

## 5. Wichtige Netzwerktools
 __________________________________________________________________________________
| Tool         | Zweck                                | Beispiel                   |
| ------------ | ------------------------------------ | -------------------------- |
| `ping`       | ICMP-Test zur Host-Erreichbarkeit    | `ping 8.8.8.8`             |
| `traceroute` | Zeigt Pfad zum Zielhost              | `traceroute tryhackme.com` |
| `nmap`       | Portscan, OS-Erkennung, Skripting    | `nmap -A -T4 10.10.10.10`  |
| `netstat`    | Aktive Verbindungen anzeigen         | `netstat -tulnp`           |
| `ip`         | IP-Konfiguration anzeigen            | `ip a`                     |
| `nslookup`   | DNS-Namenauflösung prüfen            | `nslookup example.com`     |
| `dig`        | DNS-Abfragen (Detail)                | `dig A example.com`        |
| `tcpdump`    | Netzwerkverkehr mitschneiden         | `tcpdump -i eth0`          |
| `wireshark`  | Netzwerkverkehr grafisch analysieren | GUI-Tool                   |



## 6. Netzwerkscanning
 __________________________________________________________________________
| Phase             | Tool(s)                  | Ziel                      |
| ----------------- | ------------------------ | ------------------------- |
| Ping Sweep        | `fping`, `nmap -sn`      | Lebende Hosts finden      |
| Port Scan         | `nmap`, `rustscan`       | Dienste erkennen          |
| Service Detection | `nmap -sV`, `enum4linux` | Dienstversion + Banner    |
| Packet Sniffing   | `tcpdump`, `wireshark`   | Kommunikation analysieren |
| DNS-Recon         | `dig`, `dnsrecon`        | Zonen, Subdomains         |
