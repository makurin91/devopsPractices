
# Interfaces list

* shown interfaces `ip link show`
* add interface `ip link add name eth1 type dummy`
* activate interface `ip link set eth1 up`
* delete interface `ip link set enp0s18 down`

# Add Linux bridge

* edit interfaces file `nano /etc/network/interfaces`
`auto vmbr100
iface vmbr100 inet static
        address 11.122.133.227/24
        gateway 11.122.133.1
        bridge-ports eth1
        bridge-stp off
        bridge-fd 0`
* Update settings after editing `ifup -a`
* One vmbr1 `ifup vmbr1`
* Interface info `ethtool eth1`



# Make NAT

* Enable MASQUERADE on the proxmox
`auto vmbr100
iface vmbr100 inet static
        address 192.168.100.1
        netmask 255.255.255.0
        bridge-ports none
        bridge-stp off
        bridge-fd 0
        post-up echo 1 >/proc/sys/net/ipv4/ip_forward
        post-up iptables -t nat -A POSTROUTING -s '192.168.100.0/24' -o vmbr0 -j MASQUERADE
        post-down iptables -t nat -D POSTROUTING -s '192.168.100.0/24' -o vmbr0 -j MASQUERADE`

* enable forward ipv4 `nano /etc/sysctl.conf` add `net.ipv4.ip_forward=1`

[Ubuntu]
* Open VM and edit `nano /etc/netplan/00-installer-config.yaml`
* Example 
```
network:
  version: 2
  renderer: networkd
  ethernets:
    ens18:
      addresses:
        - 192.168.100.10/24
      routes:
        - to: 0.0.0.0/0
          via: 192.168.100.1
      nameservers:
        addresses: [8.8.8.8]
      optional: true
```
* Enable netplan `netplan apply`

[Debian]
edit interfaces file `nano /etc/network/interfaces.d/`
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.100.11
    netmask 255.255.255.0
    gateway 192.168.100.1
    dns-nameservers 8.8.8.8
    up route add -net 0.0.0.0/0 gw 192.168.100.1
```
* Go to `sudo nano /etc/network/cloud-ifupdown-helper` and add `exit 0`
* and reboot `sudo reboot`
* add nameserver to the `sudo nano /etc/resolv.conf`  -> `nameserver 8.8.8.8`


* Add rule for host proxmox
`iptables -t nat -A PREROUTING -p tcp -d {white_ip} --dport 4410 -i vmbr0 -j DNAT --to-destination 192.168.100.10:22`
* Check iptables `iptables -t nat -L`
* Check iptables `iptables -t nat -L -n`
* All rules with  PREROUTING and number of lines: `iptables -t nat -L PREROUTING --line-numbers`
* Deleting if needed `iptables -t nat -D PREROUTING {number}`
* Save iptable `iptables-save`



### Networking

`sudo systemctl status systemd-networkd`
`sudo systemctl mask systemd-networkd`
`sudo systemctl status networking`

### Resolver

`systemd-resolve --status` or `resolvectl status`
`sudo nano /etc/systemd/resolved.conf`
`sudo nano /etc/resolv.conf`
`sudo systemctl restart systemd-resolved`