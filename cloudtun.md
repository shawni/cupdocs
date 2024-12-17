# Cloud-based X86 AREDN Tunnel server

## Why?
### Perhaps won't work in an emergency, but may help if located out of
 emergency zone
### Good for training
### Good for the initial event when internet might not be down yet
#### Ice storms knock out power to cell towers eventually, but tunnels will function for 24-48 hours
### Good for redundancy
### Perhaps higher bandwidth than RF links, so useful for replication
 of data when things are good

## Process
1. Create VM on cloud provider, small is fine
1. Create firewall ruleset that allows 5525/TCP and 8080/TCP inbound, bind it to VM.
1. Boot it with Finnix ISO (RAM-based Live CD), get on console.
1. wget current disk image from AREDN:
      wget http://downloads.arednmesh.org/snapshots/targets/x86/64/*combined*img.gz
1. gunzip < image_file.gz > /dev/raw_disk_device_probably_sda_or_vda
1. Reboot VM, watch boot on console, should come up in NOCALL state
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
