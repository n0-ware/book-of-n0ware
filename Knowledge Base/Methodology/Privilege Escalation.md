# Privilege Escalation

## Windows
### Enumerate Local System
***Users***
[net](../../Tools,%20Binaries,%20and%20Programs/Windows/Users%20and%20Security%20(not%20spellchecked)/net.md)
```
whoami
net users
net localgroup
net localgroup administrators
```

***File Enumeration***
```
dir /S /P "sometext" # Search one screen at a time for specific files, recursively
dir /AH /S /P # Search one screen at a time for hidden files
fir /R /S /P # Search one screen at a time for secondary data streams
tree /F
```

***Drive Enumeration***
```
fsutil fsinfo driveinfo
fsutil # in general
```

***Scheduled Tasks***
```
schtasks
```