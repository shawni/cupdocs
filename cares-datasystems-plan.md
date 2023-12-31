## CARES Data Systems Plan, v0.1

CARES intends to offer our hams and served agencies a
set of data services that will be available even in the event of local
telecommunications failure or grid down scenarios.

In order to do that, we intend to deploy redundant servers in a few key
locations in the county:

1.  Clackamas County Disaster Management, Oregon City, in the David Kidd
Ham Room.  This location serves county Disaster Management directly, plus serves one of Clackamas County's largest cities.
2.  Lake Oswego (location TBD, perhaps Fire Dept.?) Another large city
in Clackamas County.
3.  Wilsonville (facility to be completed next year).  Again, a large
city in Clackamas County.

As connectivity improves and need arises, additonally a site TBD in the
eastern portion of the county.

The goal of this effort is to enable hams to update gear, rebuild/build
needed systems, and deploy communication services even without direct
Internet access.  Additionally, CARES would like to offer limited telephony
services to served agencies, and enable familiar communications processes
to Oregon State Office of Emergency Management (OEM).

### Initial Technical Description

At each location, at least two servers will be built, capable of acting as
hypervisors for the offered services.  Virtual Machines will be proferred
as they are more self-contained and can be cloned/migrated as necessary to
other locations.

At each location, a highly-available storage server will be installed,
providing reliable storage that the hypervisors will use to 
implement their services and enable replication of data between locations.

#### Services offered

* Mesh-based PBX.  At this time, hamphone is not supported.  The purpose is
enhance communication with Oregon OEM, Clackamas Disaster Management, and
other served agencies within Clackamas County.
* Part 15 WiFi access to AREDN to support LinPhone Mesh PBX on portable devices
* File storage.  There are many uses for this, including:
  - Gold copies of necessary software in an offline environment
  - Gold copies of ham radio software and drivers
  - Operating system images as needed to reimage hardware using only the mesh
  - Documentation and manuals for ham radios and systems
  - As-needed ad-hoc storage for images and documents during an event
  - As-needed storage for Winlink and other mail systems
  - Virtual Machine images, used to provide digital services to our
    served agencies
* Winlink connectivity, at multi-megabit speeds over the mesh, but
also via a RMS Gateway that would allow communication over VHF/UHF/HF
as necessary.
* Chat functions - both meshchat (simple) and Mastodon (Slack-like, allows
  file sharing bewteen particpants
  

#### Storage replication

* The David Kidd Ham Room at the CUP in Oregon City will host the
  file replication primary copy.
* The file servers elsewhere will be kept in sync with rsync, run on a
  daily basis when there isn't an active event.  Internet based tunnels
  may be used for non-event replicaton.  An effort will be made to
  stagger updates so that links between sites are not saturated.
* At this time, the expected remote file server locations will be:
  - Lake Oswego
  - Wilsonville
* Replication during an event will be on a as-needed and on a
  as-bandwidth-is-available basis.
* Priority will be given to event-related ad-hoc files being replicated
  during an event; other files may be replicated if bandwidth and time
  permits.

#### Service Platform

* Each service offered will be enabled via a Virtual Machine running on
  one of the hypervisor servers.
* XCP-NG, with Xen Orchestra, will be the hypervisor platform of choice.
  - Managable with web browser
  - Allows VM migration between hypervisors in the event of server
    failure

