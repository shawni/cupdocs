
## David Kidd Ham Room AREDN Proxmox

Servers on the AREDN network are often actually virtual machines or
containers running on a hypervisor machine.  For CARES, we've standardized
on Proxmox VE as our hypervisor software.

Standard naming: WA7OC-PVE{number}.local.mesh.

Not recommended to run more than one PVE per ethernet segment on AREDN, since largest supported size is /27-
each server consumes an IP, as does the hypervisor.

Scripts at https://tteck.github.io/Proxmox/

Proxmox VE Tools / Proxmox VE Post Install
