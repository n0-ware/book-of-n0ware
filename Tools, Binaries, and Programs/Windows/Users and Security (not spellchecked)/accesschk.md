# accesschk.exe
###### Tags[^1]
A part of the [sysinternals](../Fundamental%20Windows%20CLI/sysinternals.md) suite of programs, `accesschk.exe` is a robust auditing tool used to obtain information on permissions operating system wide. 
## Syntax
```
C:\>accesschk [-s][-e][-u][-r][-w][-n][-v]-[f <account>,...][[-a]|[-k]|[-m]|[-p [-f] [-t]]|[-h][-o [-t <object type>]][-c]|[-d]] [[[-l|-L] [-i]]|[username]] <file, directory, event log, registry key, process, service, object>

   -a     Name is a Windows account right. Specify '*' as the name to show all
          rights assigned to a user. Note that when you specify a specific
          right, only groups and accounts directly assigned the right are
          displayed.
   -c     Name is a Windows Service e.g. ssdpsrv. Specify '*' as the
          name to show all services and 'scmanager' to check the security
          of the Service Control Manager.
   -d     Only process directories or top level key.
   -e     Only show explicitly set Integrity Levels (Windows Vista and
          higher only).
   -f     If following -p, shows full process token information including
          groups and privileges. Otherwise is a list of comma-separated
          accounts to filter from the output.
   -h     Name is a file or printer share. Specify '*' as the name to show
          all shares.
   -i     Ignore objects with only inherited ACEs when dumping full access
          control lists.
   -k     Name is a Registry key e.g. hklm\software
   -l     Show full security descriptor. Add -i to ignore inherited ACEs.
          Specify upper-case L to have the output format as SDDL.
   -m     Name is an event log (specify '*' as the name to show all event logs.
   -n     Show only objects that have no access.
   -o     Name is an object in the Object Manager namespace (default is root).
          To view the contents of a directory, specify the name with a trailing
          backslash or add -s. Add -t and an object type (e.g. section) to
          see only objects of a specific type.
   -p     Name is a process name or PID e.g. cmd.exe (specify '*' as the
          name to show all processes). Add -f to show full process
          token information including groups and privileges. Add -t to show
          threads.
   -nobanner
          Do not display the startup banner and copyright message.
   -r     Show only objects that have read access.
   -s     Recurse.
   -t     Object type filter e.g. "section"
   -u     Suppress errors.
   -v     Verbose (includes Windows Vista Integrity Level).
   -w     Show only objects that have write access.

If you specify a user or group name and path AccessChk will report the
effective permissions for that account; otherwise it will show the effective
access for accounts referenced in the security descriptor.

By default the path name is interpreted as a file system path (use the
"\pipe\" prefix to specify a named pipe path). For each object AccessChk
prints R if the account has read access, W for write access and nothing if
it has neither. The -v switch has AccessChk dump the specific
accesses granted to an account.
```

The basic usage is to provide the command a security principle name and a path to investigate. 

```
C:\Program Files\SysinternalsSuite>accesschk.exe n0_ware C:\

Accesschk v6.14 - Reports effective permissions for securable objects
Copyright ⌐ 2006-2021 Mark Russinovich
Sysinternals - www.sysinternals.com

RW C:\$AV_ASW
RW C:\$Recycle.Bin
R  C:\$Windows.~WS
R  C:\$WinREAgent
RW C:\AMD
   C:\Config.Msi
R  C:\Documents and Settings
```

The capabilities of this command are vast. Review them as you need for your use case. 

 **Common Arguments**
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 



 [^1]: #windows #fundamental #sysinternals 
