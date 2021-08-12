# Pentest Guides 

## Feching files to Windows host

Linux | Windows
-------|--------
```sudo smbserver.py -smb2support -user complexia -password complexia share $(pwd)``` | ```\\192.168.1.1\share```



## Vulnerabilities - Windows

### SeriousSam

***Setup Command***

*Running a script on a low privilege user will cause an error, run the command below*

```Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser```


**Discovery methods**

Method | Command
-------|--------
PowerShell | ```.\SeriousSam.ps1```


