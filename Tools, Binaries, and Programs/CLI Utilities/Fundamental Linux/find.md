# find

The `fin` command is a complex program designed for recursively navigating a specified portion of the file system to find files based on the specific arguments

## Syntax

```
find [search location] [arguments]
```

The `find` command can take a large number of arguments and grow very complex.

**Arguments**
- `-name` &mdash; Search by file or directory name with case sensitive syntax
- `-iname` &mdash; Search by file or directory name, ignoring case 
- `-type f/d/l/s` &mdash; Search by type - files, directories, links, sockets
- `-mtime` &mdash; Search by last modified date
- `-o` &mdash; Combine multiple values of the same argument
- `-user` &mdash; Search based on the owner
- `-perm [perms]` &mdash; Finds files where the permissions are set exactly to `[perms]`. This can take several forms and has a few operators. The default *exact* match is difficult to use with symbolic `[perms]`, and most often you will want to use either "All" `-` or "Any" `/` modes.
	- The perms can be "octal" or [Numeric Representation](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md#Numeric%20Representation%20a%20id%20numeric%20a) as in `0744` or `4000` (finds [setuid](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md#setuid) binaries) or symbolic or [character](chmod.md#Characters) based as in `-u=r`. 
	- `-perm [perms]` to find ***exactly*** these permissions. 
	- ``-perm -[perms]`` to match files where ***all***  `[perms]` are set, as in `-perm -g=w` returns files where the "group" has "write" permissions but may also have other permissions.
	- `-perm /[perms]` to match ***any*** file where the bits are set for `[perms]`.

## Examples

- `find /user/share/wordlists -type f -name *directory*`
	- Search for files that contain the name `directory` in them but may have other characters in the name inside the `/usr/share/wordlists` directory.
- `find . -type f -exec cat {} +`
	- Executes `cat` on all files in all directories in and below the current directory.
- `find / -perm 644`
	- Returns files that match this exact criterion
- `find / -perm -664`
	- Returns files where all of these bits are present. Files with `777` will match this, for example. 
- `find / -perm /222` or `find / -perm u+w,g+w,o+w` or `find / -perm u=w,g=w,o=w`
	- Finds files that are writeable by anyone, user, group, or owner. 


## Useful Finds

***Root-owned [setuid](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md#setuid) binaries***

```
find / -user root -perm -4000
```

*With write permissions*
```
find / -user root -perm -4400
```

***Root-owned [setgid](../../../Knowledge%20Base/Linux%20Fundamentals/11%20File%20Permissions.md#setgid) binaries***

```
find / -user root -perm -2000
```