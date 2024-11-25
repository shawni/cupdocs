
## The local NOCMS Winlink distribution service

Winlink is the gold standard for emergency communication in ARES.  It
adapts to many underyling carrier technologies and protocols and is
still functional in the face of regional communication disruption.

In a large event where power and/or internet connectivity is spotty
at best, the Winlink system would suffer what I will refer to as the
"thundering herd" problem, where messages queued up for distrbution
to centralized CMS would clog the narrow communication paths available.

Furthermore, local message traffic is impacted for a trimode service if
long distance (HF) communication is keeping the site busy and unable to
accept and distribute other traffic.

To address the bulk local traffic problem and to reduce load on sites
capable of long distance links, the idea of a NOCMS system was born.

These are AREDN-connected RMS servers that do not and will not attempt
to deliver to the global CMS systems, and instead sync held messages
between each other.  Because the global CMS is not involved, long distance
links are not impacted- and because the service offered is *strictly*
local-to-the-system (here in the Portland/Vancouver metro region, likely
the four counties of Washingon, Multnomah, Clackamas, and Clark),
Winlink traffic can be exchanged more efficiently.

Advantages:

1.  Any AREDN-connected Winlink Express, PAT, or other client software
can send and receive messages without regard to "is the frequency in use";
many clients can be handled simultaneously.  This property alone avoids
"thundering herd" latency issues.

2.  One or more of these RMS systems *can* include a RF component such as
VARA FM.  However, rather than needing to reach a RF-enabled site with
internet or HF access, any reachable NOCMS node will do.  If several
UHF channels spread thru the metro area were established, even RF-only
clients could exchange data with the system with less time to wait, since
there are more "lines" (frequencies) available for data exchange.

3.  Since the NOCMS nodes are syncing their message databases to
each other, local RMS outages would not destroy or make the messages
unavailable.  Clients would simply need to connect to another NOCMS node
until the down node was restored.

Disadvantages:

1.  This system would be entirely separate from the main Winlink system,
and will require some training for end users who might not understand
they have distinct uses.

2.  As proposed, during an event the communications path to OEM would
be over the existing system- while this may be slower, this also means
that anyone not aware of the NOCMS system will still get their messages
through eventually without regard to routing.

3.  There will likely be a need for some messages to be passed between
systems- probably at the county level.  This is easily done by someone
with good connectivity to both, probably at county-level EOCs.

Risks:

1.  At this time, it is unknown how many RMS databases can stay in sync
within a given time interval.  RMS can be set to sync as frequently as
one minute intervals.  Like some NoSQL databases, the promise is to have
all databases in sync eventually, where "eventually" in this case is
defined by the RMS system owners.  This is likely impacted also by how
good the links between NOCMS nodes are, and how large the messages
exchanged are.  The default sync interval is ten minutes.


