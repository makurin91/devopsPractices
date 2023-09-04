```

sudo apt-get update
sudo apt-get install net-tools

```

* Check unix socket `s` or `netstat -a -f unix`
* Check TCP socket `netstat -a -t`
* Checking the routing table `netstat -r`


* Checking the speed and duplex mode of the network card `sudo ethtool eth0` or `sudo mii-tool eth0`
* Add Duplex and speed `sudo ethtool -s eth0 speed 100 duplex full`
* 

[Checking network bandwidth]

- on the server `iperf -s`
- on the client `iperf -c <ip>`

[Measurement of transmission/reception speed for different network card modes]

- For rated speed and full duplex `iperf -c <ip> -d`
- For reduced speed and full duplex (for example 100 Mbit/s)

```

sudo ethtool -s eth0 speed 100 duplex full
iperf -c <ip> -d

```

- For reduced speed and half duplex

```

sudo ethtool -s eth0 speed 100 duplex half
iperf -c <ip> -d

```

|            Purpose             | legacy commands | iproute2 commands |
|:------------------------------:|:---------------:|:-----------------:|
| Address and link configuration |    ifconfig     | ip addr, ip link  |
|         Routing tables         |      route      |     ip route      |
|           Neighbors            |       arp       |     ip neigh      |
|              VLAN              |     vconfig     |      ip link      |
|            Tunnels             |    iptunnel     |     ip tunnel     |
|           Multicast            |     ipmaddr     |     ip maddr      |
|           Statistics           |     netstat     |        ss         |

### ping

used to test the reachability of a host on an Internet Protocol (IP) network and to measure the round-trip time for
messages sent from the originating host to a destination computer.

### traceroute

traceroute is a computer network diagnostic tool for displaying the route (path) and measuring transit delays of packets
across an Internet Protocol (IP) network.

### netstat

Displays protocol statistics and current TCP/IP network connections.

### route

route is a command used to view and manipulate the TCP/IP routing table. Manual manipulation of the routing table is
characteristic of static routing.

### arp, Address Resolution Protocol, IP to MAC address

Address Resolution Protocol (arp) is a telecommunications protocol used for resolution of network layer addresses into
link layer addresses, a critical function in multiple-access networks. ARP was defined by RFC 826 in 1982. It is
Internet Standard STD 37. It is also the name of the program for manipulating these addresses in most operating systems.

### telnet

The Telnet protocol (TELNET) is intended for the interaction of terminals and their associated processes. TELNET is
often used by terminal emulation programs to log into a remote system.

### ufw
is a simple command line to Linux's firewall features.
turn on the firewall `ufw enable`
turn off the firewall `ufw disable`
allow all connections by default `ufw default allow` 
drop all connections by default `ufw default deny`
current rules and `ufw status`
to allow traffic on port `ufw allow port`
port block `ufw deny port`
ip block `ufw deny from ip`

* Find IP Address of Network Adapter `ip_addr` or `ifconfig -a`
* Find IP Address of Router `ip route`
* Find MAC Address of Router `arp -a`
* How to turn off my network interface `ifconfig etho0 down` and `ifconfig etho0 up`
* How to set IP address `ifconfig etho0 192.168.1.86`
* How to set netmask `ifconfig netmask 255.255.255.0`
* How to find out if a network adapter is on or off? `ip link show`
* How to turn on/off a network adapter? `sudo ip link name up` and `sudo ip link name down`
* display the link and address status of active interfaces `ifconfig`
* display the link and address status of active interfaces `ip addr show`
* display all the routing table in numerical addresses `route -n`
* display all the routing table in numerical addresses `ip route show`
* display the current content of the ARP cache tables `arp`
* display the current content of the ARP cache tables `ip neigh`
* display ppp daemon log `plog`
* check the Internet connection to "yahoo.com" `ping yahoo.com`
* check who registered "yahoo.com" in the domains database `whois yahoo.com`
* trace the Internet connection to "yahoo.com" `traceroute yahoo.com` or `tracepath yahoo.com`
* trace the Internet connection to "yahoo.com" (repeatedly) `mtr yahoo.com`
* check DNS records of "example.com" by "dns-server.com" for a "a", "mx", or "any"
  record `dig [@dns-server.com] example.com [{a|mx|any}]`
* check packet filter `iptables -L -n`
* find all open ports `netstat -a`
* find listening ports `netstat -l --inet`
* find listening TCP ports (numeric) `netstat -ln --tcp`
* check DNS zone information of "example.com" `dlint example.com`
* find the ip address of a domain name. `nslookup`
* display hostname `hostname`
* displays information from wireless `iwconfig`
* scan wireless networks `sudo iwlist scan`
* reset the network `sudo /etc/init.d/networking restart`
* manual configuration `(file) /etc/network/interfaces`
* bring online interface `ifup interface` and `ifdown interface`