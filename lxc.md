# Install

`lxc-create -n <name> -t debian`

# Fix console

1. Create tty nodes:

    cd /dev
    for i in `seq 1 6`; do mknod -m 600 tty$i c 4 $i; done

2. Grant permissions in config:

    lxc.cgroup.devices.allow = c 4:0 rwm
    lxc.cgroup.devices.allow = c 4:1 rwm
    lxc.cgroup.devices.allow = c 4:2 rwm
    lxc.cgroup.devices.allow = c 4:3 rwm
    lxc.cgroup.devices.allow = c 4:4 rwm
    lxc.cgroup.devices.allow = c 4:5 rwm
    lxc.cgroup.devices.allow = c 4:6 rwm

3. Add gettty for /dev/console in /etc/inittab:

    0:2345:respawn:/sbin/getty 38400 console

# Shutting down

1. `poweroff` inside lxc first

2. `lxc-stop -n <name>`
