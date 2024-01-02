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
