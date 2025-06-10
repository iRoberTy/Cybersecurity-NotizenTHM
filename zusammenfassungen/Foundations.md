# 🛡️ Foundations of Cybersecurity – Principles & Models

## 1. CIA-Triad: Confidentiality, Integrity, Availability

### 📌 Confidentiality
- Schutz vor **unbefugtem Zugriff** auf Informationen.
- Methoden: **Verschlüsselung, Zugangskontrollen, Rollenmanagement (RBAC)**.
- Ziel: **Vertraulichkeit sensibler Daten wahren**.

### 📌 Integrity
- Gewährleistung der **Korrektheit & Unverfälschtheit** von Daten.
- Schutz vor **Manipulation** durch Hashes, digitale Signaturen, Checksums.
- Ziel: **Daten sollen nur autorisiert veränderbar sein**.

### 📌 Availability
- **Zugänglichkeit von Systemen & Daten** bei Bedarf sicherstellen.
- Maßnahmen: **Redundanz, DDoS-Schutz, Backup-Systeme**.
- Ziel: **Betriebssicherheit auch bei Störungen**.

---

## 2. DAD-Triad: Disclosure, Alteration, Destruction/Denial

Der **Gegenpol** zur CIA-Triad – definiert sicherheitsrelevante **Verletzungen**:

### 🚨 Disclosure
- **Unbefugte Offenlegung** von Informationen.
- → Verletzt die **Vertraulichkeit**.

### 🚨 Alteration
- **Unbefugte Veränderung** von Informationen.
- → Verletzt die **Integrität**.

### 🚨 Destruction/Denial
- **Zerstörung oder Verhinderung** des Zugriffs auf Daten/Systeme.
- → Verletzt die **Verfügbarkeit**.

---

## 3. Security Models: Bell-LaPadula

### 📘 Bell-LaPadula Model (1970er, MIL-SPEC)
- Ziel: Schutz **vertraulicher Informationen** durch Zugriffskontrollen.
- Fokussiert auf **Confidentiality**, nicht Integrität oder Verfügbarkeit.

#### Grundprinzipien:
- **"No Read Up" (NRU)**: Subjekte dürfen keine Daten auf höherem Level lesen.
- **"No Write Down" (NWD)**: Subjekte dürfen nicht auf niedrigeren Levels schreiben (um Datenlecks zu verhindern).

> ⚠️ Typisch für **Militär & Geheimdienste**, wo Informationsklassifizierung zentral ist.

---

## 4. Security Principles

### 🛡️ Defence-in-Depth
- Sicherheitsstrategie mit **mehreren, gestaffelten Schutzmaßnahmen**.
- Beispiel: Firewall + IDS + Authentifizierung + Logging.
- Idee: **Falls eine Maßnahme versagt, greifen weitere Schutzebenen.**

### 🧱 Zero Trust
- **"Never trust, always verify"**.
- Jeder Benutzer/Service muss **authentifiziert, autorisiert & überwacht** werden – unabhängig von Standort oder Netzwerk.
- Grundlage für moderne **Cloud- und Remote-Security-Konzepte**.

### 🔍 Trust but Verify
- Klassisches Sicherheitsprinzip: **Vertrauen ist gut, Kontrolle ist besser.**
- Besonders wichtig bei **internen Nutzern** & Dienstleistern.
- Kombiniert menschliche Vertrauenskultur mit **technischer Überwachung**.

---

## 5. ISO/IEC 19249:2017 – Security Design Principles

- Internationale Norm zur **Standardisierung sicherer Systemarchitektur**.
- Fokus auf:  
  - **Least Privilege**  
  - **Fail-Safe Defaults**  
  - **Open Design**  
  - **Separation of Duties**
  - **Minimize Attack Surface**

> 📘 Ziel: Wiederverwendbare Design-Prinzipien für **vertrauenswürdige IT-Systeme**.

---

## 6. Begriffsdifferenzierung: Vulnerability, Threat, Risk

| Begriff        | Definition                                                                 |
|----------------|-----------------------------------------------------------------------------|
| **Vulnerability** | Schwachstelle im System (z. B. ungepatchter Server, schwaches Passwort)     |
| **Threat**        | Potenzieller Angreifer / Angriff, der eine Schwachstelle ausnutzen kann   |
| **Risk**          | Wahrscheinlichkeit + Schadenshöhe, dass eine Schwachstelle ausgenutzt wird |

### 🔁 Beispiel:
- **Vulnerability:** veraltete Websoftware  
- **Threat:** Angreifer mit Exploit  
- **Risk:** Datenklau bei Erfolg → hoch

---



# 🚨 Incident Response – Grundlagen & Ablaufplan

## 🧭 1. Was ist Incident Response?

**Incident Response (IR)** ist der strukturierte Prozess zur **Erkennung, Analyse und Bewältigung von IT-Sicherheitsvorfällen**, mit dem Ziel, den Schaden zu minimieren, Systeme wiederherzustellen und aus Vorfällen zu lernen.

---

## 🧱 2. Zielsetzung der Incident Response

- **Schnelle Erkennung** von Sicherheitsvorfällen
- **Eindämmung der Auswirkungen**
- **Beseitigung der Bedrohung**
- **Wiederherstellung des Normalbetriebs**
- **Lerngewinn zur Prävention zukünftiger Vorfälle**

---

## 📉 3. Arten von Sicherheitsvorfällen

- **Malware-Infektionen (z. B. Ransomware)**
- **Phishing & Social Engineering**
- **Data Breaches & Datenlecks**
- **Insider Threats**
- **Denial-of-Service (DoS/DDoS)**
- **Unbefugter Systemzugriff (z. B. durch Exploits)**

---

## 🔁 4. Incident Response Lifecycle (nach NIST SP 800-61r2)

### 🛠️ 1. Preparation
- Richtlinien, Verfahren, Tools, Schulungen
- Beispiel: **IR-Policy, Forensik-Toolkits, Playbooks**

### 🔍 2. Detection & Analysis
- Vorfall identifizieren, validieren und priorisieren
- Quellen: IDS, SIEM, Logs, Usermeldungen

### ⛓️ 3. Containment
- Vorfall eindämmen, z. B. durch:
  - Netzwerktrennung
  - Account-Deaktivierung
  - Blockieren von IPs/Ports

### 🧹 4. Eradication
- Ursache entfernen:
  - Malware löschen
  - Schwachstellen patchen
  - Hintertüren eliminieren

### ♻️ 5. Recovery
- Systeme wiederherstellen (Backups, Reimaging)
- Monitoring intensivieren
- Validieren der Bereinigung

### 📚 6. Lessons Learned
- Bericht schreiben
- Schwachstellenanalyse
- Verbesserung der Sicherheitsmaßnahmen

---

## 🛡️ 5. Incident Response Team (IRT/CSIRT/SOC)

| Rolle                  | Aufgabe                              |
|------------------------|--------------------------------------|
| **Incident Handler**   | Koordination & Kommunikation         |
| **Forensiker**         | Spurensicherung & Analyse            |
| **Netzwerkadmin**      | Firewall, Trennung, Logging          |
| **Management**         | Kommunikation, Freigaben             |
| **Legal / Datenschutz**| Meldepflichten prüfen (z. B. DSGVO)  |

---

## 📊 6. Wichtige Tools & Quellen

- **SIEM-Systeme:** Splunk, Graylog, ELK
- **Netzwerk-Tools:** Wireshark, Zeek, tcpdump
- **Forensik:** Volatility, Autopsy, FTK Imager
- **Malware-Analyse:** Cuckoo Sandbox, CyberChef
- **Threat Intelligence:** MITRE ATT&CK, VirusTotal

---

## ⚖️ 7. Rechtlicher Rahmen (Deutschland/EU)

- **DSGVO Artikel 33**: Meldepflicht bei Datenpannen innerhalb 72 Stunden
- **BSI-Gesetz / KRITIS-Verordnung**: Meldung schwerwiegender IT-Störungen an das BSI
- **ISO/IEC 27035**: Standard für Incident Response Management

---

## 🔁 8. Best Practices

- **Playbooks pro Angriffstyp (Malware, Phishing, etc.)**
- **Logging & Monitoring von Anfang an aktiv**
- **Kommunikationsplan (intern/extern)**
- **Regelmäßige IR-Übungen (Tabletops / Red Team)**

---



# 📜 Logging in der IT-Sicherheit – Grundlagen & Best Practices

## 🔍 1. Was sind Logs?

**Logs (Protokolle)** sind strukturierte Aufzeichnungen über Ereignisse in IT-Systemen. Sie sind zentrale Werkzeuge zur **Überwachung, Analyse, Fehlerbehebung** und vor allem zur **Erkennung von Sicherheitsvorfällen (Incident Detection).**

---

## 🛡️ 2. Warum sind Logs sicherheitsrelevant?

- **Beweissicherung bei Angriffen (Forensik)**
- **Früherkennung von Angriffen (Threat Detection)**
- **Nachvollziehbarkeit von Benutzeraktionen**
- **Überwachung kritischer Systeme**
- **Pflichterfüllung bei Audits & Compliance (z. B. DSGVO, ISO 27001)**

---

## 🧱 3. Wichtige Log-Typen nach Systemebene

### 🖥️ System-Logs
- **/var/log/syslog** (Debian) oder **/var/log/messages** (RHEL)
- Bootvorgänge, Kernel-Events, Gerätefehler

### 👥 Authentifizierungs-Logs
- **/var/log/auth.log** (Debian)
- SSH-Logins, Sudo-Nutzung, PAM-Events

### 🌐 Netzwerk- & Firewall-Logs
- **iptables, ufw, pf, Windows Firewall**
- Eingehende/ausgehende Verbindungen, Port Scans, Blockierungen

### 🌍 Webserver-Logs
- **Apache:** `/var/log/apache2/access.log`  
- **Nginx:** `/var/log/nginx/access.log`  
- Informationen über Anfragen, Pfade, IPs, Statuscodes

### 📦 Applikations-Logs
- Fehler oder Zugriffsmuster in Custom-Apps (z. B. Webshop, API)
- Logging-Frameworks: **log4j, journald, rsyslog**

### 🪟 Windows-Event-Logs
- Über **Event Viewer** einsehbar:
  - **Security** (z. B. Logins)
  - **System** (Dienste, Hardware)
  - **Application** (App-bezogene Events)

---

## 📈 4. Zentralisierte Log-Auswertung (SIEM)

**SIEM = Security Information and Event Management**

Beispiele:
- **Splunk**, **ELK Stack (Elasticsearch, Logstash, Kibana)**, **Graylog**
- Automatisierung von Alarmen, Korrelation von Ereignissen

---

## ⚙️ 5. Logging Best Practices

### ✅ Aktivieren & strukturieren
- Stelle sicher, dass **alle sicherheitsrelevanten Logs aktiv sind**
- Verwende **einheitliches Format** (JSON, Common Log Format)

### ✅ Zeitsynchronisation (NTP)
- **Logs ohne konsistente Zeitangaben** sind forensisch wertlos

### ✅ Zugriffsschutz
- Nur autorisierte Nutzer dürfen Logs lesen/schreiben
- **Audit-Logs dürfen niemals veränderbar sein**

### ✅ Rotation & Archivierung
- Automatisch rotieren und **ältere Logs sichern oder anonymisieren**

### ✅ Frühwarnsysteme
- Erkenne Auffälligkeiten früh durch:
  - **Brute-Force-Versuche**
  - **ungewöhnliche Anmeldezeiten**
  - **häufige Fehlermeldungen**

---

## 🧠 6. Log-Analyse: Was ist verdächtig?

| Indikator                    | Bedeutung                                |
|-----------------------------|-------------------------------------------|
| Mehrfache Login-Fehler      | Möglicher Brute-Force-Angriff             |
| SSH-Logins als root         | Ungewöhnlich, hohes Risiko                |
| Viele 404-Fehler            | Pfad-Scanning, Recon-Phase                |
| Zugriff aus fremden Ländern | Möglicher kompromittierter Account        |
| Ungewöhnliche Cron-Jobs     | Persistenz durch Angreifer                |

---

## 📚 7. Normen & rechtliche Grundlagen

- **DSGVO**: Nur notwendige Daten erfassen, Aufbewahrungsfristen beachten
- **ISO/IEC 27001**: Logging als Teil des Informationssicherheits-Managements (ISMS)
- **BSI Grundschutz**: Logging & Monitoring sind obligatorisch

---

