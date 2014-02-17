# Daemon user

Create a daemon user with identical group id and group name:
    groupadd -g $uid $name
    useradd -M -u $uid -g $uid -s /sbin/nologin -d / $name

# Console IM

    wall # broadcast to all users
    write someone # write to someone
    mesg n # prevent others from writing to you
    mesg y # opposite of above; allow
    talk # THE original instant messenger

# Networking diagnosis

    lsof -i:123 # List port 123; sudo is required if port is well-known (eg. 80)
    ping example.com # THE ping command: host connectivity test
    ping 8.8.8.8 # IP address is also accepted, of course
    traceroute example.com # ping each node (router, switch, or whatever) along the route to a certain host
    traceroute 8.8.8.8
    traceroute -n 8.8.8.8 # By default, traceroute tries to translate IP addresses to domain names. Specify -n to prevent this.


Wireshark remote capture:

    ssh root@remote-host tshark -w - not tcp port 22 | wireshark -k -i -

# LDAP

    ldapsearch -H host -D binddn [ -w passwd | -W ] -b base filter

# LVM

You may need to run `vgscan` and then `vgchange -a y vgname` to "activate" LVM.

Specify the kernel `root` parameter like: ``/dev/mapper/vgname-lvname``

# Disk & File

    df # usage of file systems
    du # size of directory
    du -csh *

# Firewalling

## Simple IP blocking: hosts.allow and hosts.deny

When a request is received hosts.allow is checked first, then hosts.deny; when
neither matched, the default is to allow.
