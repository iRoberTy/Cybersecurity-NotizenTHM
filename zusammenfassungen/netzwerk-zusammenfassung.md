# 🌐 Netzwerk-Zusammenfassung

## 1. Was ist ein Netzwerk?
Ein Netzwerk ist eine Gruppe von Geräten (Hosts), die miteinander kommunizieren, um Daten auszutauschen.  
Ziel: Ressourcen teilen (Drucker, Dateien, Internetzugang etc.)

---

## 2. Wichtige Begriffe

| Begriff | Erklärung |
|--------|-----------|
| IP-Adresse | Eindeutige Adresse eines Geräts im Netzwerk (z. B. `192.168.1.1`) |
| MAC-Adresse | Physische Hardware-Adresse (z. B. `00:1A:2B:3C:4D:5E`) |
| Port | Virtuelle Schnittstelle für Netzwerkdienste |
| Protokoll | Regeln für Datenübertragung (z. B. TCP, UDP) |
| Subnetz | Teilbereich eines Netzwerks (z. B. `192.168.1.0/24`) |
| Gateway | Vermittler zwischen Netzwerken |
| DNS | Domain Name System – löst Namen in IPs auf |

---

## 3. OSI-Modell (7 Schichten)

| Schicht | Funktion | Beispiel |
|--------|----------|----------|
| 7 – Anwendung | Nutzerinteraktion | HTTP, FTP, SMTP |
| 6 – Darstellung | Übersetzung, Verschlüsselung | SSL, JPEG |
| 5 – Sitzung | Verbindungsverwaltung | NetBIOS, RPC |
| 4 – Transport | Zuverlässigkeit | TCP, UDP |
| 3 – Netzwerk | Routing | IP, ICMP |
| 2 – Sicherung | MAC, Frames | Ethernet, Switches |
| 1 – Bitübertragung | Elektrische Signale | Kabel, Hubs |

---

## 4. TCP vs. UDP

| Merkmal | TCP | UDP |
|--------|-----|-----|
| Verbindung | Verbindungsorientiert | Verbindungslos |
| Zuverlässigkeit | Ja | Nein |
| Geschwindigkeit | Langsamer | Schneller |
| Anwendung | HTTP, FTP, SSH | DNS, VoIP, Streaming |

---

## 5. Wichtige Netzwerktools

| Tool | Zweck |
|------|--------|
| `ping` | Prüft Host-Erreichbarkeit |
| `traceroute` | Zeigt Verbindungsweg |
| `nmap` | Portscanner |
| `netstat` | Verbindungen & offene Ports |
| `ip` / `ifconfig` | IP-Konfiguration |
| `dig`, `nslookup` | DNS-Abfragen |
