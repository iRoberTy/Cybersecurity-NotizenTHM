# 🪟 Windows Grundlagen & Security Commands

| Befehl                  | Zweck                          |
| ----------------------- | ------------------------------ |
| `ipconfig /all`         | Netzwerkinfos (IP, DNS, MAC)   |
| `netstat -ano`          | Offene Verbindungen & PIDs     |
| `tasklist`              | Aktive Prozesse                |
| `taskkill /PID [id]`    | Prozess beenden                |
| `whoami`                | Aktueller Benutzer             |
| `net user`              | User-Accounts auflisten        |
| `net user [username] *` | Passwort ändern                |
| `systeminfo`            | Systeminformationen anzeigen   |
| `Get-Process` (PS)      | Prozesse anzeigen (PowerShell) |
| `Get-Service` (PS)      | Dienste anzeigen (PowerShell)  |
|                          \\\\\\\\\\\\\\\\\\\\\\\          \\\\\\\\\\\\\\\\\
| ----------------------------------------------- | ------------------------ |
| `ping [ip]`                                     | Host erreichbar?         |
| `tracert [ip]`                                  | Route verfolgen          |
| `netsh advfirewall firewall show rule name=all` | Firewall-Regeln anzeigen |
| `netsh interface ip show config`                | Netzwerkkonfiguration    |

| Methode                    | Befehl / Ansatz                    |
| -------------------------- | ---------------------------------- |
| Lokaler Admin prüfen       | `net localgroup administrators`    |
| Dienstrechte prüfen        | `sc qc [ServiceName]`              |
| Passwörter auslesen        | Mimikatz (PowerShell / executable) |
| Powershell-Remoting prüfen | `Get-PSSessionConfiguration`       |
| Scheduled Tasks auslesen   | `schtasks /query /fo LIST /v`      |

| Speicherort    | Zweck                                             |
| -------------- | ------------------------------------------------- |
| Event Logs     | `eventvwr.msc` oder via Powershell `Get-WinEvent` |
| Registry       | `reg query` / `regedit` für Autostart etc.        |
| Prefetch Files | Schnelle Programmanalyse                          |
| Autoruns       | Auto-Start Programme erkennen (Sysinternals Tool) |


# 🐧 Linux Grundlagen & Security Commands

| Befehl            | Zweck                              |
| ----------------- | ---------------------------------- |
| `ip a`            | Netzwerkinterfaces anzeigen        |
| `netstat -tulnp`  | Offene Ports & zugehörige Prozesse |
| `ps aux`          | Alle Prozesse anzeigen             |
| `top` / `htop`    | Prozesse interaktiv überwachen     |
| `df -h`           | Festplattenbelegung                |
| `mount`           | Gemountete Laufwerke anzeigen      |
| `cat /etc/passwd` | Benutzerliste anzeigen             |
| `cat /etc/shadow` | Passwort-Hashes (nur root)         |
| `whoami`          | Aktueller Benutzer                 |
| `sudo -l`         | Rechte des Users anzeigen          |
|                    \                                    \\
| ------------------- | ----------------------------------- |
| `ping [ip]`         | Host erreichbar?                    |
| `traceroute [ip]`   | Route verfolgen                     |
| `iptables -L`       | Firewall-Regeln anzeigen            |
| `ss -tulnp`         | Offene Ports & Prozesse anzeigen    |
| `nmap -sC -sV [ip]` | Schneller Scan mit Serviceerkennung |

| Methode                    | Befehl / Ansatz                           |
| -------------------------- | ----------------------------------------- |
| Sudo-Rechte prüfen         | `sudo -l`                                 |
| SUID / SGID Dateien finden | `find / -perm -4000 -type f 2>/dev/null`  |
| Welt-beschreibbare Dateien | `find / -perm -o=w -type f 2>/dev/null`   |
| Cronjobs überprüfen        | `cat /etc/crontab` / `ls -la /etc/cron.*` |
| Umgebungsvariablen prüfen  | `env`                                     |

| Datei               | Zweck                       |
| ------------------- | --------------------------- |
| `/var/log/auth.log` | Authentifizierungs-Logs     |
| `/var/log/syslog`   | Systemmeldungen             |
| `/var/log/kern.log` | Kernel-Logs                 |
| `.bash_history`     | Kommando-Historie des Users |
| `last`              | Login-Verlauf               |



| Tool          | Zweck                                | Plattform   |
| ------------- | ------------------------------------ | ----------- |
| `netcat`      | Netzwerk-Tool (Port-Listener, Shell) | Win / Linux |
| `nmap`        | Netzwerkscanner                      | Win / Linux |
| `tcpdump`     | Paket-Sniffer                        | Linux       |
| `Wireshark`   | GUI Paket-Analyse                    | Win / Linux |
| `PowerSploit` | Windows Post-Exploitation Framework  | Windows     |
| `Metasploit`  | Exploit-Framework                    | Win / Linux |
| `Responder`   | LLMNR/NBT-NS Poisoning               | Win / Linux |
