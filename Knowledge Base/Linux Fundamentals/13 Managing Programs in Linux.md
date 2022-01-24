# Managing Programs in Linux
Earlier we talked about [Processes](12%20Processes%20and%20Monitoring.md#Processes) in *Linux*, how to monitor, list, and kill them. But how do these programs/applications/services get on the system in the first place? It is important to remember that from a simple command to a web browser, everything is considered a program. A piece of shellcode with two lines in it that uses `echo` to pipe text into a new file is a program. 

On *Linux*, there is a concept of "packages."[^1]Packages help deliver and maintain new software for *Linux-based* operating systems. In a nutshell, a package contains all the files necessary to install and configure a program on *Linux*. The tool [apt](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/apt.md) (*Advanced Package Tool*) is the primary package manager many *Linux* versions such as *Ubuntu, Debian*, and other related systems on *Linux*.

> `apt` actually uses another tool, [dpkg](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/dpkg.md), at its core to manage the installation and removal of packages. `apt` is simply more responsive and use friendly and is therefore more widely used.

Packages are very effective in large part because of the varying *Linux* operating systems. *Linux* is not a "one-size-fits-all" environment. Programs require various dependencies, essentially files or components in the form of other packages required for programs to run correctly. A package can get the information on which dependencies are required to run it, and install those dependencies as part of the install process. It is truly a remarkable process. 

[apt](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/apt.md) plays a major part in this, helping identify, organize, download, and install related dependencies and the desired application all in one. "APT" helps navigate the myriad of complementary and conflicting dependencies required to keep a system functioning. For example, if I install a program that requires `useful-library-1.1.0` but I only have `useful-library-1.0.0`, `apt` can help get the right programs installed. 

## Repositories

To use `apt`, we need to have up-to-date lists of the packages available, and these are kept in repositories. Each *Linux* distribution comes with a list of repositories and remote locations from which it can update those repository lists. These remote locations can be added to in ways that differ distro to distro, but the main way `apt` keeps them updated is the same, with the argument [update](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/apt.md#update) (requires [sudo](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/sudo.md) permissions). 

```
apt update
```

Running this command often is a good practice as it will keep the list of available packages current, assisting when we want to install new programs. The list of the available packages is cached locally, and includes information related to versions, descriptions, dependencies, and so on. 

Repositories are listed in the `/etc/apt` folder, typically in the `sources.list` or `sources.list.d/` directory. 

The `sources.list` file on *Kali Linux* looks like this, for example. 

```
┌──(kali㉿kali)-[/etc/apt]
└─$ cat sources.list       
# See https://www.kali.org/docs/general-use/kali-linux-sources-list-repositories/
deb http://http.kali.org/kali kali-rolling main contrib non-free

# Additional line for source packages
# deb-src http://http.kali.org/kali kali-rolling main contrib non-free
```

The current list of main repositories is maintained at `http://http.kali.org/kali kali-rolling main contrib non-free` and is the standard *Kali* list. This list can be added to as needed to include other repositories.[^2]

## Program Management

Managing programs on your OS requires updating, upgrading, searching, and removing in various circumstances. `apt` has tools for all of these, and maintains its useful organization schema and helpfulness for each situation.

To upgrade packages, dependencies, we can run [upgrade](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/apt.md#upgrade) (requires [sudo](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/sudo.md) permissions).

```
sudo apt upgrade
```

To view specific information regarding your locally cached repositories and available programs, we can use the [cache](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/apt.md#cache) argument. 

```
apt-cache search [program]
```

This can return a lot of information as it uses a simple keyword search. It is also worth noting that `cache` searches the description of a package, not the package title, meaning you can return packages related to, but not specified, your keyword. These packages are related in some way and may be add-ons, dependencies, or otherwise. 

To install programs, we use the [install](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/apt.md#install) argument (requires [sudo](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/sudo.md) privileges).

```
┌──(kali㉿kali)-[~]
└─$ sudo apt install net-tools 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
```

Removing programs requires the [remove](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/apt.md#remove) argument, with the optional `--purge` flag to remove everything related to the program, including config files. Without `--purge`, only the program is removed. 

```
┌──(kali㉿kali)-[~]
└─$ sudo apt remove net-tools
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
```

The [autoremove](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/apt.md#autoremove) argument helps us by removing a list of packages that `apt` knows no longer need to be on the system, and can be removed in one go with this argument:

```
┌──(kali㉿kali)-[~/Documents/GitHub/course-notes]
└─$ sudo apt autoremove                   
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  fastjar gnome-desktop3-data jarwrapper kali-wallpapers-2021.4 libaom0 libcbor0 libcodec2-0.9 libfluidsynth2
  libfmt7 libgdal29 libgdk-pixbuf-xlib-2.0-0 libgdk-pixbuf2.0-0 libgnome-desktop-3-19 libigdgmm11 libjsoncpp24
  libodbc1 libodbccr2 libqhull8.0 libspdlog1 liburing1 libvpx6 libwireshark14 libwiretap11 libwsutil12
  libxkbregistry0 linux-image-5.10.0-kali9-amd64 linux-image-5.14.0-kali2-amd64 maltego odbcinst odbcinst1debian2
  python3-orjson ruby-atomic ruby-thread-safe starkiller zaproxy
0 upgraded, 0 newly installed, 35 to remove and 0 not upgraded.
```

## dpkg

The core tool used to install [programs](../../../Knowledge%20Base/Linux%20Fundamentals/13%20Managing%20Programs%20in%20Linux.md) in *Linux* is `dpkg`.[^3] The program [[../../Tools, Binaries, and Programs/CLI Utilities/Fundamental Linux/apt]] uses `dpkg` at its core to [install](../../Tools,%20Binaries,%20and%20Programs/CLI%20Utilities/Fundamental%20Linux/apt.md#install) packages on your behalf. However, it is possible to use `dpkg` directly to install programs on *Linux* via `.deb` files you've directly downloaded. The "man" page for `dpkg` describes it as *"a tool to install, build, remove and manage Debian packages."* This pretty neatly sums it up. 

The core arguments for `dpkg` are `-i` to install a `.deb` file and `-r` to remove or `-P` to purge a package, and it requires `sudo` privileges. 


[^1]: https://www.lifewire.com/guide-to-linux-packages-2202801]
[^2]:https://www.kali.org/docs/general-use/kali-linux-sources-list-repositories/
[^3]:https://www.journaldev.com/43603/dpkg-command-in-linux