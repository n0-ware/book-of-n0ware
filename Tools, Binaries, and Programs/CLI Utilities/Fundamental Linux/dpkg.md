# dpkg
The core tool used to install [programs](../../../Knowledge%20Base/Linux%20Fundamentals/13%20Managing%20Programs%20in%20Linux.md) in *Linux* is `dpkg`.[^1] The program [[apt]] uses `dpkg` at its core to [install](apt.md#install) packages on your behalf. However, it is possible to use `dpkg` directly to install programs on *Linux* via `.deb` files you've directly downloaded. The "man" page for `dpkg` describes it as *"a tool to install, build, remove and manage Debian packages."* This pretty neatly sums it up. 

## Syntax

```
dpkg [arguments] [package name]
```

**Arguments**
- `-i` &mdash; Install a `.deb` package from a file, removing any previously installed older versions of the package
- `-r` &mdash; Remove a package, including every file related to the package except any "config" files
- `-P` &mdash; Purage a package, including all files and configuration files
- `--update-avail` &mdash; Updates all available packages stored in the `dpkg` repositories.


[^1]:https://www.journaldev.com/43603/dpkg-command-in-linux