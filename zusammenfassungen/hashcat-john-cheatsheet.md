# 🔐 Hashcat & John the Ripper Cheatsheet

## 🚀 Hashcat Befehle (Grundlagen)

| Zweck | Befehl |
|-------|--------|
| Grundstruktur | `hashcat -m [Modus] -a [Angriffsart] -o [Output] [Hash-Datei] [Wortliste]` |
| Beispiel (MD5 + Wortliste) | `hashcat -m 0 -a 0 hashes.txt rockyou.txt` |
| Resume nach Abbruch | `hashcat --restore` |
| Modus anzeigen (Hashtypen) | `hashcat --help | grep -i hash-mode` |
| Beispiel mit SHA1 | `hashcat -m 100 -a 0 sha1.txt rockyou.txt` |
| Regeln anwenden | `hashcat -m 0 -a 0 -r rules/best64.rule hashes.txt rockyou.txt` |
| Benchmark (alle Algorithmen) | `hashcat -b` |
| Geräte anzeigen | `hashcat -I` |
| Output-Format: nur Klartext | `--show` |
| Beispiel: Klartext anzeigen | `hashcat -m 0 --show -o cracked.txt hashes.txt` |


---

## 🧠 John the Ripper Befehle

| Zweck | Befehl |
|-------|--------|
| Basic Crack | `john hashes.txt` |
| Mit Format (z. B. SHA1) | `john --format=raw-sha1 hashes.txt` |
| Wortliste angeben | `john --wordlist=rockyou.txt hashes.txt` |
| Regeln aktivieren | `john --wordlist=rockyou.txt --rules hashes.txt` |
| Fortschritt ansehen | `john --status` |
| Ergebnisse anzeigen | `john --show hashes.txt` |
| Gecrackte Passwörter löschen | `john --wipe` |
| Liste unterstützter Formate | `john --list=formats` |
| Hash vorbereiten (z. B. /etc/shadow) | `unshadow passwd shadow > hashes.txt` |

---

## 🔧 Nützliche Zusatzbefehle

| Zweck | Befehl |
|-------|--------|
| Hash extrahieren mit grep | `grep -oE '[a-f0-9]{32,64}' input.txt > hashes.txt` |
| Hash in richtiges Format bringen (John) | `echo 'password' | openssl passwd -1 -stdin` |
| Hash-Format testen | `hashid` oder `hash-identifier` (Python-Tools) |

---

**Tipp:** Kombiniere Hashcat und John mit starken Wortlisten wie `rockyou.txt` und mit `hashid` identifizieren!
