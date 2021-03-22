# LinuxPrivEsc
Linux Privilege Escalation techniques &amp; resources

- [Enumeration](#enumeration)
  - [system enum](#system-enum)
  - [user enum](#user-enum)
  - [network enum](#network-enum)
  





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
