# journalctl
The `journalctl` command is used to view *systemd* logs[^1]. There are several ways to filter and use this command

## Syntax

Alone, `journalctl` will simply list the log files starting with the beginning of the log file. This will create pages and pages of files.

```
journalctl [options]
```

**Arguments**
- `-utc` &mdash; Displays timestamps in `utc` format
- `-b [boot]` &mdash; Display logs from current boot or `[boot]` number or ID
- `--list-boots` &mdash; 
- `--since` &mdash; List logs from a date using `YYY-MM-DD HH:MM:SS` format. Alternatively, you can use strings such as `yesterday` or `"1 hour ago"`. 
- `--until` &mdash; Follows the same format above, often combined with `--since` 
- `-u [service]` &mdash; Filter by service of interest, such as `apache2` or `sshd` or `nginx.service`
- `_PID, _UID, _GID [id #]` &mdash; List by PID
- `-r` &mdash; View in reverse order (newest first) 
- `-f` &mdash; Print new entries as they come in, like [watch](../Fundamental%20Linux/watch.md) 

And many, many more. 

[^1]:https://www.freedesktop.org/wiki/Software/systemd/