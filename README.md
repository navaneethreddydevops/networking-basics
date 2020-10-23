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

```
nmcli device show

GENERAL.DEVICE:                         ens5
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         02:93:D4:D3:56:61
GENERAL.MTU:                            9001
GENERAL.STATE:                          100 (connected)
GENERAL.CONNECTION:                     System ens5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         172.31.117.107/20
IP4.GATEWAY:                            172.31.112.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 172.31.112.1, mt = 100
IP4.ROUTE[2]:                           dst = 172.31.112.0/20, nh = 0.0.0.0, mt = 100
IP4.DNS[1]:                             172.31.0.2
IP4.DOMAIN[1]:                          us-west-1.compute.internal
IP6.ADDRESS[1]:                         2600:1f1c:2bf:6400:d319:54c0:7900:e207/128
IP6.ADDRESS[2]:                         fe80::93:d4ff:fed3:5661/64
IP6.GATEWAY:                            fe80::dc:bcff:fe49:79ce
IP6.ROUTE[1]:                           dst = 2600:1f1c:2bf:6400::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::dc:bcff:fe49:79ce, mt = 100
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[5]:                           dst = 2600:1f1c:2bf:6400:d319:54c0:7900:e207/128, nh = ::, mt = 100

GENERAL.DEVICE:                         lo
GENERAL.TYPE:                           loopback
GENERAL.HWADDR:                         00:00:00:00:00:00
GENERAL.MTU:                            65536
GENERAL.STATE:                          10 (unmanaged)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --
IP4.ADDRESS[1]:                         127.0.0.1/8
IP4.GATEWAY:                            --
IP6.ADDRESS[1]:                         ::1/128
IP6.GATEWAY:                            --
```

```
ip route show  --- Gives the route of default gateway

default via 172.31.112.1 dev ens5 proto dhcp metric 100 
172.31.112.0/20 dev ens5 proto kernel scope link src 172.31.117.107 metric 100
```
```
routel         --- Gives the entire routing information

        target            gateway          source    proto    scope    dev tbl
        default       172.31.112.1                     dhcp            ens5 
  172.31.112.0/ 20                  172.31.117.107   kernel     link   ens5 
      127.0.0.0          broadcast       127.0.0.1   kernel     link     lo local
     127.0.0.0/ 8            local       127.0.0.1   kernel     host     lo local
      127.0.0.1              local       127.0.0.1   kernel     host     lo local
127.255.255.255          broadcast       127.0.0.1   kernel     link     lo local
   172.31.112.0          broadcast  172.31.117.107   kernel     link   ens5 local
 172.31.117.107              local  172.31.117.107   kernel     host   ens5 local
 172.31.127.255          broadcast  172.31.117.107   kernel     link   ens5 local
            ::/ 96     unreachable                                       lo 
::ffff:0.0.0.0/ 96     unreachable                                       lo 
    2002:a00::/ 24     unreachable                                       lo 
   2002:7f00::/ 24     unreachable                                       lo 
   2002:a9fe::/ 32     unreachable                                       lo 
   2002:ac10::/ 28     unreachable                                       lo 
   2002:c0a8::/ 32     unreachable                                       lo 
   2002:e000::/ 19     unreachable                                       lo 
2600:1f1c:2bf:6400:d319:54c0:7900:e207                                      kernel            ens5 
2600:1f1c:2bf:6400::/ 64                                       ra            ens5 
   3ffe:ffff::/ 32     unreachable                                       lo 
        fe80::/ 64                                   kernel            ens5 
        default    fe80::dc:bcff:fe49:79ce                       ra            ens5 
        default        unreachable                   kernel              lo 
            ::1              local                   unspec              lo local
2600:1f1c:2bf:6400:d319:54c0:7900:e207              local                   unspec              lo local
fe80::93:d4ff:fed3:5661              local                   unspec              lo local
        ff00::/ 8                                                      ens5 local
        default        unreachable                   kernel              lo 
```

```
# To check if network manager is running
systemctl status NetworkManager
```

```
Network Topology
```

### Connection TroubleShooting

# Vlan MAC Addressing Tools

```
rping
```
# Address Routing and Network Authentication Tools

```
traceroute
tracepath
```

# Blocked Ports and Firewalls

```
ss
telnet
tcpdump
nc
```

# DNS Tools

```
dig 
dig amazon.com
```

# Server Ports that are serving

```
ss -lntp
ss -lntp | grep 443
ss -lntp | grep 80   # For webserver quick check if port of nginx is open
ss -lntp | grep 22   # For SSH deamon check
```

# CURL Basics

```
curl -I 10.127.10.1
```

# Check what services is running
```
systemctl status {firewalld,iptables}
```

# Firewall

```
firewall-cmd --list-all   ### Show all services that are added to firewall

firewall-cmd --permanent --add-service=httpd ### To add service to firewall of localhost

firewall-cmd --reload
```

# Route Tables 

```
route -n 
# Adding the both interfaces on host to route tables
ip route add 10.0.1.0/24 dev eth0 tab 1  # Adding the subnet cidrs to routetable of table1 on eth0 (Local Network Interface)
ip route add 10.0.1.0/24 dev eth2 tab 2  # Adding the subnet cidrs to routetable of table2 on eth1 (Additional Local Network Interface)

ip route show tab 1
ip route show tab 2

ip rule add from 10.0.1.0/24 tab 1
ip rule add from 10.0.1.0/24 tab 2
```