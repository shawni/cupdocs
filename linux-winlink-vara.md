# Linux Winlink Express + VARA FM

## Why?
### Windows 10 off support, Windows 11 too tied to cloud + online
### Good for training

## Process
1. Install Zorin OS 18 on computer, preferable i5+ with 8GB RAM, storage as needed but at least 120GB
1. Install Bottles- go to 
1. Edit /etc/config/network - move lan and dtdlink to eth1 VLANS (ok if eth1 doesn't exist)
   Move eth0 to br-wan; reboot node.
1. "fw3 flush" -- in case default firewall rules are in the way.
1. Create /etc/aredn_include/bridge.network.user and wan.network.user per documentation:
bridge.network.user:
"""

config device
      option name 'br0'
      option type 'bridge'
      option vlan_filtering '1'
      list ports 'eth2'

"""
wan.network.user:
"""

config device
        option name 'br-wan'
        option type 'bridge'
        list ports 'eth0'
                                        
config interface wan
        option device 'br-wan'
        option proto 'dhcp'
                                        
"""
lan.network.user:
"""

config device
        option name 'br-lan'
        option type 'bridge'
        list ports 'eth1'

config interface lan
        option device 'br-lan'
        option proto 'static'
        option ipaddr '10.1.2.3'
        option netmask '255.255.255.248'

1. Configure node using WAN IP now as per normal.  Node will reboot. 
1. Since aredn_include files are already present, bridges will be configured such that wan interface is functional.
