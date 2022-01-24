# Advanced Package Tool Manager (apt)

See [Managing Programs in Linux](../../../Knowledge%20Base/Linux%20Fundamentals/13%20Managing%20Programs%20in%20Linux.md) for more information on *Linux* packages. 

## Syntax

To keep package information up to date, run:

### update
```
┌──(kali㉿kali)-[~]
└─$ sudo apt update && sudo apt upgrade -y
Get:1 http://dl.google.com/linux/chrome/deb stable InRelease [1,811 B]
Get:2 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1,093 B]    
Get:3 http://kali.download/kali kali-rolling InRelease [30.6 kB]
Get:4 http://kali.download/kali kali-rolling/main amd64 Packages [17.8 MB]
Get:5 http://kali.download/kali kali-rolling/main amd64 Contents (deb) [40.7 MB]
Get:6 http://kali.download/kali kali-rolling/contrib amd64 Packages [114 kB]
Get:7 http://kali.download/kali kali-rolling/contrib amd64 Contents (deb) [153 kB]
Get:8 http://kali.download/kali kali-rolling/non-free amd64 Packages [212 kB]
Get:9 http://kali.download/kali kali-rolling/non-free amd64 Contents (deb) [1,017 kB]
```

Here you can see the various remote repositories `apt` is including for its update. 

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

The current list of main repositories is maintained at `http://http.kali.org/kali kali-rolling main contrib non-free` and is the standard *Kali* list. [^1]

### upgrade

To upgrade all installed packages and core system functionalities, run:
```
┌──(kali㉿kali)-[~]
└─$ sudo apt upgrade   
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
73 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  fastjar gnome-desktop3-data jarwrapper kali-wallpapers-2021.4 libaom0 libcbor0 libcodec2-0.9 libfluidsynth2
  libfmt7 libgdal29 libgdk-pixbuf-xlib-2.0-0 libgdk-pixbuf2.0-0 libgnome-desktop-3-19 libigdgmm11 libjsoncpp24
  libodbc1 libodbccr2 libqhull8.0 libspdlog1 liburing1 libvpx6 libwireshark14 libwiretap11 libwsutil12
  libxkbregistry0 linux-image-5.10.0-kali9-amd64 linux-image-5.14.0-kali2-amd64 maltego odbcinst odbcinst1debian2
  python3-orjson ruby-atomic ruby-thread-safe starkiller zaproxy
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  python3-aiosmb
The following packages will be upgraded:
  amass amass-common apt apt-utils bsdextrautils bsdutils crackmapexec eject fakeroot fdisk flameshot
  gir1.2-nm-1.0 google-chrome-stable iproute2 kali-desktop-base kali-themes kali-themes-common kali-tweaks
  libapt-pkg6.0 libasound2 libasound2-data libblkid1 libexpat1 libexpat1-dev libfakeroot libfdisk1 libfido2-1
  libical3 libinput-bin libinput10 libmount1 libneon27-gnutls libnm0 libnss-systemd libpam-systemd libprocps8
  librtlsdr0 libsdl2-2.0-0 libsmartcols1 libsystemd0 libudev1 libuuid1 libuv1 libuv1-dev libxnvctrl0 libxxhash0
  mount network-manager nmap nmap-common pgcli procps python3-aiowinreg python3-asysocks python3-minidump
  python3-minikerberos python3-mistune python3-msldap python3-nacl python3-pypykatz python3-winacl rfkill
  shared-mime-info systemd systemd-sysv tasksel tasksel-data udev util-linux xserver-common xserver-xorg-core
  xserver-xorg-legacy xvfb
```

If you supply a single package after `upgrade`, `apt` will only upgrade that program and its associated packages. 

System administrators must be careful not to run global upgrades without backups as this can cause system failures if certain programs running locally require older package or dependency versions, in which case they will break if an unsupported version is installed. 

> `apt` maintains a list of packages that can be removed with [autoremove](#autoremove).

### cache

The *cache* in `apt` stores information related to the packages `apt` knows about. If you want to install an application, it is good to know if this is present in your *Linux* repository list. Run this command to find out

```
apt-cache search [program]
```

`apt` will return information in a "keyword search" format, meaning you can return a large amount of information if you search for something generic, such as `apache`. 

```
┌──(kali㉿kali)-[~]
└─$ apt-cache search apache                                                                    
alpine - Text-based email client, friendly for novices but powerful
alpine-doc - Text-based email client's documentation
ant - Java based build tool like make
ant-contrib - collection of tasks, types and other tools for Apache Ant
ant-doc - Java based build tool like make - API documentation and manual
ant-optional - Java based build tool like make - optional libraries
apache-users - Enumerate usernames on systems with Apache UserDir module
apache2 - Apache HTTP Server
apache2-bin - Apache HTTP Server (modules and other binary files)
apache2-data - Apache HTTP Server (common files)
apache2-dev - Apache HTTP Server (development headers)
apache2-doc - Apache HTTP Server (on-site documentation)
avro-bin - Apache Avro C utilities (avro-c)
...
```

Certain items were returned here that do not contain "apache" in their title, and this is because `cache` looks for the keyword in the description of the package, not in the title. These items are related, such as `avro-bin`. 

### show

To obtain additional information on a specific package, we can use the `show` command

```
┌──(kali㉿kali)-[~]
└─$ apt show avro-bin 
Package: avro-bin
Version: 1.9.0-1+b1
Priority: optional
Section: utils
Source: avro-c (1.9.0-1)
Maintainer: Robert Edmonds <edmonds@debian.org>
Installed-Size: 73.7 kB
Depends: libavro23, libc6 (>= 2.4)
Homepage: https://avro.apache.org
Download-Size: 12.0 kB
APT-Sources: http://http.kali.org/kali kali-rolling/main amd64 Packages
Description: Apache Avro C utilities (avro-c)
 Apache Avro is a data serialization system. Avro provides rich data
 structures; a binary data format; and a container file format, to store
 Avro-encoded data persistently.
...
```

### install

To install a package with `apt`, we use the `install` command. A common suite of programs installed on *Linux* are the `net-tools` programs, containing programs such as `traceroute`. We would install these with the command

```
┌──(kali㉿kali)-[~]
└─$ sudo apt install net-tools 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
...
```

### remove

Removing programs with `apt` is equally easy and can be done in two ways. The first requires only the `remove` arguemtn, which removes the program but often leaves a small "config" file behind in case the program is installed again. 

```
┌──(kali㉿kali)-[~]
└─$ sudo apt remove net-tools
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
```

### autoremove

Similar to `remove`, `autoremove` is used to "trim" packages and dependencies that are no longer necessary for the system. For whatever reason, such as the removal of a program or the update of another that renders current dependencies unnecessary, sometimes packages need to be removed. `apt` maintains a list of this, and they can be removed with this argument:

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


[^1]:https://www.kali.org/docs/general-use/kali-linux-sources-list-repositories/