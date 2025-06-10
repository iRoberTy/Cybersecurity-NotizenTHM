# 🔐 Hashcat
GPU-basiertes Passwort-Cracking. Schnell & skriptbar.

hashcat -m [Modus] -a [Angriff] -o cracked.txt hashes.txt wordlist.txt

| Aktion                | Befehl                                     |
| --------------------- | ------------------------------------------ |
| Wortlistenmodus (MD5) | `hashcat -m 0 -a 0 hashes.txt rockyou.txt` |
| Regeln aktivieren     | `-r rules/best64.rule`                     |
| Resume nach Abbruch   | `hashcat --restore`                        |
| Gecrackte anzeigen    | `hashcat -m 0 --show hashes.txt`           |
| Benchmarks & Geräte   | `hashcat -b` / `hashcat -I`                |
| Hash-Modi anzeigen    | `hashcat --help | grep -i hash-mode`       |


# 🧠 John the Ripper
CPU-basiertes Cracking mit vielen Formaten & Shadow-Support

john --wordlist=rockyou.txt hashes.txt

| Aktion                      | Befehl                                |
| --------------------------- | ------------------------------------- |
| Automatischer Start         | `john hashes.txt`                     |
| Format spezifizieren        | `--format=raw-sha1`                   |
| Regeln aktivieren           | `--rules`                             |
| Fortschritt anzeigen        | `--status`                            |
| Ergebnisse anzeigen/löschen | `--show` / `--wipe`                   |
| Shadow-Dateien vorbereiten  | `unshadow passwd shadow > hashes.txt` |


# 🧰 Hash-Analyse & Tools

| Tool                | Zweck                              |
| ------------------- | ---------------------------------- |
| `hashid`            | Hashtyp erkennen (mehrere Matches) |
| `hash-identifier`   | Python-GUI zur Hash-Erkennung      |
| `grep`              | Hashes extrahieren (Regex!)        |
| `openssl passwd -1` | MD5-Hash erzeugen                  |


# --------------------------------------------------- 🕵️‍♂️ Wordlist-Creation & Web Brute Force ---------------------------------------------------
# 🔍 Gobuster
Directory/Web-Bruteforce

gobuster dir -u https://target -w /usr/share/wordlists/dirb/common.txt

| Modus         | Befehl                                         |
| ------------- | ---------------------------------------------- |
| Verzeichnisse | `gobuster dir -u URL -w wordlist.txt`          |
| DNS           | `gobuster dns -d domain.com -w subdomains.txt` |


# 🔨 Hydra
Login-Bruteforcer (parallelisiert, viele Protokolle)

hydra -l admin -P rockyou.txt ftp://10.10.10.10

| Protokolle | Beispiele                                                                |
| ---------- | ------------------------------------------------------------------------ |
| HTTP-Form  | `-f http-post-form "/login:username=^USER^&password=^PASS^:F=Incorrect"` |
| FTP / SSH  | `-P rockyou.txt -t 4 ftp://10.10.10.10`                                  |


# 🧬 CeWL
Custom Wordlists durch Webseiten-Crawling

cewl https://target.com -w wordlist.txt

| Optionen  | Zweck               |
| --------- | ------------------- |
| `-d 2`    | Crawltiefe          |
| `-m 5`    | Mindestwortlänge    |
| `--email` | E-Mails extrahieren |


# 📁 Crunch
Wordlist-Generator

crunch 6 8 abcdef123 -o customlist.txt

| Beispiel                 | Wirkung                                      |
| ------------------------ | -------------------------------------------- |
| `crunch 6 6 123456`      | Alle 6-stelligen Kombinationen aus 1-6       |
| `crunch 8 8 -t admin@@@` | Wordlist mit Platzhaltern (z. B. `admin123`) |
