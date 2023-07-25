
# Interfaces list

* shown interfaces `ip link show`
* add interface `ip link add name eth1 type dummy`
* activate interface `ip link set eth1 up`

# Add Linux bridge

* edit interfaces file `nano /etc/network/interfaces`
`auto vmbr100
iface vmbr100 inet static
        address 51.119.126.217/24
        gateway 51.119.126.1
        bridge-ports eth1
        bridge-stp off
        bridge-fd 0`
* Update settings after editing `ifup -a`
* One vmbr1 `ifup vmbr1`
* Interface info `ethtool eth1`



# Another schema

* Enable MASQUERADE
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
* Add rule for host proxmox
`iptables -t nat -A PREROUTING -p tcp -d {white_ip} --dport 4410 -i vmbr0 -j DNAT --to-destination 192.168.100.10:22`

* Check iptables `iptables -t nat -L`

* Rule for containers
`iptables -t nat -A PREROUTING -p tcp -d {host_white_ip} --dport 4410 -i vmbr0 -j DNAT --to-destination {container_ip}:22`