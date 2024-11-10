
## Serve-stale BIND 9 server config ##

These files are intended to be dropped into a bog-standard Debian 12.x
bind9 installation, in /etc/bind.

/etc/bind/named.conf.local defines the mesh local zone (the default) and
indicates which node to forward queries to, i.e. the IP address of the
nearest node running AREDN with dnsmasq- this is the IP inside the
"forwarders" stanza.  Multiple IP addresses, each with a semicolon suffix,
can be listed here for redundancy purposes, though all of them should be
net-close to the BIND server.

/etc/bind/named.conf.options defines the address to forward all other zone
queries towards (it may or may not be the local node) and enables the
serve-stale functionality.  By default it caches stale entries for a week,
and attempts to refresh the cache any time a stale entry is queried.

Also in named.conf.options, DNSSEC configuration to explicitly exclude mesh
name space from DNSSEC validation.  Since the name space can't be anchored
to the public root and there is no ability to anchor the .local.mesh. namespace
within AREDN (the dnsmasq servers can't do DNSSEC RR types), this has to
be done in order to allow BIND to function in this limited environment.

In the expected environment, the only contents of /etc/bind/named.conf are
include statements for these two files and "/etc/bind/named.conf.default-zones"
which we don't modify from the included default.


