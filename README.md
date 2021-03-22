# LinuxPrivEsc
Linux Privilege Escalation techniques &amp; resources

- [Enumeration](#enumeration)
  - [system enum](#system-enum)
  - [user enum](#user-enum)
  - [network enum](#network-enum)
- [password hunting](#password-hunting)
- [Automated tools](#automated-tools)
  - [linpeas](#linpeas)
  - [linenum](#linenum)
  - [linux exploit suggestor](#linux-exploit-suggestor)
  - [Linuxprivchecker](#linuxprivchecker)



# 
## Enumeration

We assume that first exploited & have access to the m/c,
But the user is non admin. now we have to go through the stages of 5
stage methodlogy to escalate the priviledge .

### System enum

`uname -a` // look for version & search for exploit

`cat /etc/issuse` // look for distribution

`cat /proc/version`

`lscpu`

`ps aux`

**what kernel are we on ? is it vuln to anything arch?**

### User enum

we're going to find out who we are, what permissions we have & what we're capable of doing.

`whoami`

`id`

`sudo -l` // list out what commands we can run as sudo

`cat passwd / shadow / groups` // what file we can access

`history`

**look for sudo escalations**

`sudo su -`

### Network enum

Net enum is important in a sense that it lets us see what the ip architecture is, what ports are open,what we're interacting with.

`ip a` 

sometimes a network can have two adapters in it, or might have nic's in, dual netwok.

`ip route` // to check the route

**check for arp table**

`ip neigh`

**what ports are open & what communication exists?**

`netstat -ano`

check which mc's are talking to the target & if needed to exploit or listen to trafic etc. 

#

## Password hunting

### Colour code search items

`grep --color=auto -rnw '/' -ie "PASSWORD" --color=always 2> /dev/null`

color the word password wherever it finds.

`locate password` // search for file named password (be creative like pass, pwd etc)

`find /name id_rsa 2> /dev/null`

get decent in searching through files

best enums are like going through 100s & 1000s of line just to find the password.

look for interesting files that might contain password.

#
## Automated Tools

## Linpeas
https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS

### Basic Usage

```sh
curl wget https://raw.githubusercontent.com/carlospolop/privilege-escalation-awesome-scripts-suite/master/linPEAS/linpeas.sh | sh
```

## LinEnum

https://github.com/rebootuser/LinEnum

https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh

### Basic Usage

```sh
./LinEnum.sh -s -k keyword -r report -e /tmp/ -t
```

## Linux Exploit suggestor

https://github.com/mzet-/linux-exploit-suggester

### Usage & example output

```sh
./les.sh
```
```sh
Possible Exploits:

[+] [CVE-2019-13272] PTRACE_TRACEME

   Details: https://bugs.chromium.org/p/project-zero/issues/detail?id=1903
   Exposure: highly probable
   Tags: ubuntu=16.04{kernel:4.15.0-*},ubuntu=18.04{kernel:4.15.0-*},debian=9{kernel:4.9.0-*},[ debian=10{kernel:4.19.0-*} ],fedora=30{kernel:5.0.9-*}
   Download URL: https://github.com/offensive-security/exploitdb-bin-sploits/raw/master/bin-sploits/47133.zip
   ext-url: https://raw.githubusercontent.com/bcoles/kernel-exploits/master/CVE-2019-13272/poc.c
   Comments: Requires an active PolKit agent.
```
## Linuxprivchecker py
https://github.com/sleventyeleven/linuxprivchecker

### Usage

```sh
python linuxprivchecker.py
```
