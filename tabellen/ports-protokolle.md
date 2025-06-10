# 📊 Ports & Protokolle – Merktabelle
 ________________________________________________________________________________
| Port  |Protokoll|         Dienst          | Typ |         Beschreibung         |
|-------|---------|-------------------------|-----|------------------------------|
| 20/21 |   FTP   |      File Transfer      | TCP |      Dateiübertragung        |
|   22  |   SSH   |      Remote Access      | TCP |        Sichere Shell         |
|   23  |  Telnet |  Fernzugang (unsicher)  | TCP |           Veraltet           |
|   25  |   SMTP  |       Mailversand       | TCP |        E-Mail senden         |
|   53  |   DNS   |     Namensauflösung     | U/T |         Domain → IP          |
| 67/68 |   DHCP  |       IP-Vergabe        | UDP |       Client ↔ Server        |
|   69  |   TFTP  |       Trivial FTP       | UDP | Dateiübertragung (ohne Auth) |
|   80  |   HTTP  |     Web (unsicher)      | TCP |Webseiten ohne Verschlüsselung|
|   88  | Kerberos|    Authentifizierung    | TCP |           AD Logins          |
|  110  |   POP3  |      Mail-Empfang       | TCP |   Lokale E-Mail-Zustellung   |
|  123  |   NTP   |      Zeitabgleich       | UDP |  Systemzeit synchronisieren  |
|137–139| NetBIOS |     Windows Dienste     | T/U |     Datei-/Druckdienste      |
|  143  |   IMAP  |      Mail-Zugriff       | TCP |    Serverbasierte E-Mail     |
|161/162|   SNMP  |   Netzwerkmonitoring    | UDP |      Geräte-Management       |
|  389  |   LDAP  |   Verzeichnisdienste    | TCP | AD - Querying und Enumeration|
|  443  |  HTTPS  |Sichere Web-Kommunikation| TCP |   SSL/TLS-Verschlüsselung    |
|  445  |   SMB   | Datei- & Druckfreigabe  | TCP |  Windows Netzwerkfreigaben   |
|  636  |  LDAPS  |       LDAP + TLS        | TCP |          AD Zugriff          |
| 1900	|  SSDP   |    Discovery (UPnP)	    | UDP |    IOT / HomeNet Scanning    |
| 3306  |  MySQL  |     Datenbankzugang     | TCP |        SQL-Datenbank         |
| 3389  |   RDP   |     Remote Desktop      | TCP |   GUI-Zugriff auf Windows    |
| 5353	|  mDNS   |        Multicast DNS    | UDP |   Lokale Netzwerkerkennung   | 
| 5985	|WinRM_80 | Remote Mgmt (Windows)	| TCP |      PowerShell Remote       |
| 5986	|WinRM_443|	  Remote Mgmt (TLS)	    | TCP | Encrypted PowerShell Remote  |
| 8080	|HTTP-Alt |  Alternative HTTP-Port	| TCP |       Oft für Web-UIs        |
| 8443	|HTTPS-Alt|	  Sicherer Webzugriff	| TCP |    Admin-Panels, Tools       | 
 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


## 🔐 Häufige Pentesting-Ziele

- **22 (SSH)** → Brute-Force, schwache Passwörter
- **445 (SMB)** → EternalBlue, Pass-the-Hash
- **80/443 (HTTP/HTTPS)** → XSS, SQLi, LFI, RCE
- **21 (FTP)** → Anonymous Login, File Disclosure
- **53 (DNS)** → Zonenübertragung, Spoofing

Port-Gruppierungen für besseren Überblick:

Netzwerkverwaltung: SNMP, NTP, DHCP

Windows-Dienste: SMB, RDP, NetBIOS, WinRM, LDAP

Web Services: HTTP/S, 8080, 8443

Remote Access: SSH, Telnet, RDP

Dateiübertragung: FTP, TFTP, NFS, SMB

Mail: SMTP, POP3, IMAP