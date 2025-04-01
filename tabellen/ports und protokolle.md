# 📊 Ports & Protokolle – Merktabelle

| Port | Protokoll | Dienst | Typ | Beschreibung |
|------|-----------|--------|-----|--------------|
| 20/21 | FTP | File Transfer | TCP | Dateiübertragung |
| 22 | SSH | Remote Access | TCP | Sichere Shell |
| 23 | Telnet | Fernzugang (unsicher) | TCP | Veraltet |
| 25 | SMTP | Mailversand | TCP | E-Mail senden |
| 53 | DNS | Namensauflösung | UDP/TCP | Domain → IP |
| 67/68 | DHCP | IP-Vergabe | UDP | Client ↔ Server |
| 69 | TFTP | Trivial FTP | UDP | Dateiübertragung (ohne Auth) |
| 80 | HTTP | Web (unsicher) | TCP | Webseiten ohne Verschlüsselung |
| 110 | POP3 | Mail-Empfang | TCP | Lokale E-Mail-Zustellung |
| 123 | NTP | Zeitabgleich | UDP | Systemzeit synchronisieren |
| 137–139 | NetBIOS | Windows Dienste | TCP/UDP | Datei-/Druckdienste |
| 143 | IMAP | Mail-Zugriff | TCP | Serverbasierte E-Mail |
| 161/162 | SNMP | Netzwerkmonitoring | UDP | Geräte-Management |
| 443 | HTTPS | Sichere Web-Kommunikation | TCP | SSL/TLS-Verschlüsselung |
| 445 | SMB | Datei- & Druckfreigabe | TCP | Windows Netzwerkfreigaben |
| 3306 | MySQL | Datenbankzugang | TCP | SQL-Datenbank |
| 3389 | RDP | Remote Desktop | TCP | GUI-Zugriff auf Windows |

---

## 🔐 Häufige Pentesting-Ziele

- **22 (SSH)** → Brute-Force, schwache Passwörter
- **445 (SMB)** → EternalBlue, Pass-the-Hash
- **80/443 (HTTP/HTTPS)** → XSS, SQLi, LFI, RCE
- **21 (FTP)** → Anonymous Login, File Disclosure
- **53 (DNS)** → Zonenübertragung, Spoofing

