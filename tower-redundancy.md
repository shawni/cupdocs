
## Remote tower AREDN node redundancy

Certain AREDN nodes may be installed on towers or locations where access
to the radio is highly restricted, difficult, or both.  In order to
allow upgrades to AREDN nodes to proceed in a manner such that errors do
not affect connectivity, we propose the following guidelines.

1.  AREDN nodes in this situation will be deployed in pairs, with two
antenna aligning identically.  One radio, the standby, will be set to
a channel that will not interfere with the primary, and at low power.

1.  The primary radio will be updated to new firmware and logically put
in a probationary status.  The standby radio will NOT be upgraded yet.

1.  If the primary radio functions correctly for a month, the standby
can be upgraded.  

1.  If the primary fails, power is removed by unplugging the POE or
otherwise configuring smart power (power injector plugged into smart
power, et cetera) to remove power.

1.  The standby will be reconfigured with the TX power and channel setting
of the primary, and rebooted to serve in place until the primary can be
repaired.

