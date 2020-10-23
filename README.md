# networking-basics
networking-basics

```
ifconfig --- Give the eth0 interface and loopback

ens5: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 172.31.117.107  netmask 255.255.240.0  broadcast 172.31.127.255
        inet6 2600:1f1c:2bf:6400:d319:54c0:7900:e207  prefixlen 128  scopeid 0x0<global>
        inet6 fe80::93:d4ff:fed3:5661  prefixlen 64  scopeid 0x20<link>
        ether 02:93:d4:d3:56:61  txqueuelen 1000  (Ethernet)
        RX packets 4760  bytes 689671 (673.5 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4946  bytes 1060356 (1.0 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 16  bytes 1036 (1.0 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16  bytes 1036 (1.0 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
```
ip addr show --- Give the eth0 interface and loopback

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: ens5: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc mq state UP group default qlen 1000
    link/ether 02:93:d4:d3:56:61 brd ff:ff:ff:ff:ff:ff
    inet 172.31.117.107/20 brd 172.31.127.255 scope global noprefixroute dynamic ens5
       valid_lft 3114sec preferred_lft 3114sec
    inet6 2600:1f1c:2bf:6400:d319:54c0:7900:e207/128 scope global noprefixroute dynamic 
       valid_lft 419sec preferred_lft 119sec
    inet6 fe80::93:d4ff:fed3:5661/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```
```
nmcli --- Gives Detailed Information of eth0 interface and loopback

ens5: connected to System ens5
        "Amazon.com Elastic"
        ethernet (ena), 02:93:D4:D3:56:61, hw, mtu 9001
        ip4 default, ip6 default
        inet4 172.31.117.107/20
        route4 0.0.0.0/0
        route4 172.31.112.0/20
        inet6 2600:1f1c:2bf:6400:d319:54c0:7900:e207/128
        inet6 fe80::93:d4ff:fed3:5661/64
        route6 2600:1f1c:2bf:6400::/64
        route6 ::/0
        route6 ff00::/8
        route6 fe80::/64
        route6 2600:1f1c:2bf:6400:d319:54c0:7900:e207/128

lo: unmanaged
        "lo"
        loopback (unknown), 00:00:00:00:00:00, sw, mtu 65536

DNS configuration:
        servers: 172.31.0.2
        domains: us-west-1.compute.internal
        interface: ens5

Use "nmcli device show" to get complete information about known devices and
"nmcli connection show" to get an overview on active connection profiles.
```