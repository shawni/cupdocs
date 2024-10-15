
## David Kidd Ham Room AREDN Procedures

We are currently cloning the MAC address of one of the laptops to the
hAP (kd7zdo-hap-02) in order to present a known address to the County
network gear; this grants all devices that use the hAP as a gateway to
get the same acess as the original laptop did.


Before updating the kd7zdo-hap-02 node, double check the WAN Ethernet
address.

1.  From another AREDN lan device, ssh to the node:

```ssh -p 2222 root@kd7zdo-hap-02```

2.  Examine the mesh network configuration, and look for the br-wan stanza:

```more /etc/config/network```

```
 config device
 	option name 'br-wan'
. 	option type 'bridge'
 	option macaddr 84:A9:38:D2:0C:C5  # DKHR
 	list ports 'br0.4'

# option macaddr DC:2C:6E:4A:E6:9A
```

3.  In the above stanza, the commented out macaddr is the one that would
be used if it wasn't overridden (you can verify by removing all macaddr
commands and rebooting; when you can reconnect and look at this file,
it should have the lower macaddr within the "option device" stanza.

3a.
```
 config device
 	option name 'br-wan'
 	option type 'bridge'
 	option macaddr 84:A9:38:D2:0C:C6  # DKHR number 2
 	list ports 'br0.4'

```

4.  The above macaddr that is NOT commented out is the one that the County
network devices know belong to the DKHR and should be preserved across
upgrades.  Make a note of it before the upgrade (it should be this one).

5.  Upgrade the node as per AREDN usual instructions.

6.  Reconnect to the node and edit /etc/config/network, replacing the
macaddr line with the saved one for device br-wan.

7.  Save and reboot.  This will remain until the next upgrade or full reconfigure (if you reset the node to zero).


