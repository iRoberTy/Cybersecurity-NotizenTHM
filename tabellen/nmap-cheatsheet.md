nmap [Optionen] [Ziel]
Ziel: IP, IP-Range (z.B. 192.168.1.0/24), Domain, Datei mit Zielen (-iL targets.txt)
 __________________________________________________________________________________________________________
| Scan-Typ                | Beschreibung                                      | Beispiel                   |
| ----------------------- | ------------------------------------------------- | -------------------------- |
| TCP SYN Scan (Standard) | Schneller halb-offener Scan (Stealth)             | `nmap -sS 10.0.0.1`        |
| TCP Connect Scan        | Vollständiger TCP Handshake (weniger stealthy)    | `nmap -sT 10.0.0.1`        |
| UDP Scan                | Scan von UDP-Ports (langsamer)                    | `nmap -sU 10.0.0.1`        |
| FIN Scan                | FIN-Flag zum Umgehen mancher Firewalls            | `nmap -sF 10.0.0.1`        |
| Xmas Scan               | TCP-Flags FIN, URG, PSH gesetzt                   | `nmap -sX 10.0.0.1`        |
| Null Scan               | Kein TCP-Flag gesetzt (stealth)                   | `nmap -sN 10.0.0.1`        |
| ACK Scan                | Prüft Firewall-Regeln und Filter                  | `nmap -sA 10.0.0.1`        |
| Window Scan             | TCP Window-Size Analyse (Firewall-Umgehung)       | `nmap -sW 10.0.0.1`        |
| Maimon Scan             | TCP FIN/ACK Paket                                 | `nmap -sM 10.0.0.1`        |
| Idle Scan               | Blindscan über drittes System (stealth, Spoofing) | `nmap -sI zombie 10.0.0.1` |
| Option                   \\\\\\\\                                   ////////
| -------------------------------- | ------------------------------- |
| `-p 22,80,443`                   | Nur bestimmte Ports scannen     |
| `-p-`                            | Alle 65535 Ports scannen        |
| `-p U:53,111,137,T:21-25,80,139` | Gemischter TCP und UDP Portscan |

| Option                  | Zweck                                         |
| ----------------------- | --------------------------------------------- |
| `-sV`                   | Versionsscan: Dienste und Versionen ermitteln |
| `--version-intensity 5` | Detailgrad des Versionsscans steuern (0–9)    |
|                   //////                                      //////////
| ---------------- | ----------------------------------------- |
| `-O`             | OS-Fingerprinting durchführen             |
| `--osscan-guess` | Unsichere OS-Erkennung mit Annahmen       |
| `--osscan-limit` | Nur bei offenen Ports OS-Scan durchführen |
|                   \\\\\                                       \\\\
| ---------------------- | ---------------------------------------- |
| `--source-port 53`     | Quellport auf DNS-Port setzen            |
| `--data-length 20`     | Padding zum Payload hinzufügen           |
| `--scan-delay 1s`      | Verzögerung zwischen Paketen             |
| `--randomize-hosts`    | Zufällige Reihenfolge der Hosts          |
| `--spoof-mac [Vendor]` | MAC-Adresse faken (z.B. `--spoof-mac 0`) |
|                     ///                                            \\\\\\\\\\\
| ------------------ | -------------------------------------------------------- |
| `-oN output.txt`   | Normale Ausgabe in Datei                                 |
| `-oX output.xml`   | XML-Ausgabe                                              |
| `-oG output.gnmap` | Grepable Ausgabe                                         |
| `-oA output`       | Alle Formate speichern (`output.nmap`, `.xml`, `.gnmap`) |
|                    /                                             /////////////
| ----------------- | ------------------------------------------- |
| `-Pn`             | Kein Ping vor Scan (Host als „up“ annehmen) |
| `-sL`             | DNS-Auflösung, ohne zu scannen              |
| `--traceroute`    | Traceroute durchführen                      |
| `--reason`        | Gründe für Portstatus anzeigen              |
| `--packet-trace`  | Pakete beim Senden/Empfangen anzeigen       |
| `--append-output` | Output an bestehende Dateien anhängen       |
| `--exclude [IPs]` | IPs vom Scan ausschließen                   |
| `--min-rate [n]`  | Minimale Paketrate (Pro Sekunde)            |
|         //////////                                      ////////
| ------ | --------------------------------------------- |
| `-T0`  | Sehr langsam, max. Vorsicht (Firewall-Bypass) |
| `-T1`  | Sehr langsam                                  |
| `-T2`  | Langsam                                       |
| `-T3`  | Normal (Standard)                             |
| `-T4`  | Schnell (für LAN)                             |
| `-T5`  | Sehr schnell (leicht auffällig)               |
|         \\\\\\\\\\\\                                    \\\\\\\\\\\\\\\\
| ------------------- | ------------------------------------------------- |
| `-sC`               | Standard-Skripte (ähnlich wie `--script=default`) |
| `--script [Name]`   | Bestimmtes Script ausführen (z.B. `http-title`)   |
| `--script-args`     | Parameter für Scripts                             |
| `--script-trace`    | Zeigt Debug-Ausgaben von Scripts                  |
| `--script-updatedb` | NSE Datenbank aktualisieren                       |
 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

# 1. Schneller TCP SYN Scan der häufigsten 1000 Ports
nmap -sS -T4 10.10.10.1
# 2. Komplettscan aller TCP Ports, OS Detection, Version und Scripting
nmap -p- -A 10.10.10.1
# 3. UDP Scan mit Versionsinfo (langsamer)
nmap -sU -sV 10.10.10.1
# 4. Scan eines Subnetzes mit Ping-Scan (nur Erreichbarkeit prüfen)
nmap -sn 192.168.1.0/24
# 5. Scan mit Exploit- und Vuln-Scan Script
nmap --script vuln 10.10.10.1
# 6. DNS Brute Force (via NSE Script)
nmap --script dns-brute -v target.com
# 7. SMB OS Discovery & User Enumeration (NSE)
nmap --script smb-os-discovery,smb-enum-users -p445 10.10.10.1
# 8. Scan mit TCP Null Scan und Quellport 53 (Firewall-Bypass)
nmap -sN --source-port 53 10.10.10.1
# 9. Scan mit Paket-Trace und Ausgabe in XML
nmap -sS --packet-trace -oX scan.xml 10.10.10.1
# 10. Idle Scan über Zombie Host (Stealth Scan)
nmap -sI zombiehost 10.10.10.1


-sS: TCP SYN Scan (Standard & stealth)
-sT: TCP Connect Scan (weniger stealth)
-sU: UDP Scan (langsamer, aber wichtig)
-A: Aggressive Scan (OS, Version, Scripts, Traceroute)
-Pn: Ping deaktivieren, Hosts als aktiv annehmen
--script: NSE-Scripts ausführen