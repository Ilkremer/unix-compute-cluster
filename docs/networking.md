# Network Architecture

## Current layout

The earlier planned three-node sketch is superseded by four Debian nodes on
the same OpenWrt network. The owner reports this topology as in use:

```text
Upstream network / Internet
            |
    Raspberry Pi CM4
     OpenWrt gateway
            |
     Ethernet switch
            |
            +-- headnode   (Dell Vostro 260)
            +-- compute01  (Dell OptiPlex 755)
            +-- compute02  (Lenovo ThinkCentre M78)
            +-- compute03  (Lenovo ThinkCentre M57)
```

This is logical connectivity, not a specification of CM4 interfaces, VLANs,
address ranges, or verified upstream settings. The CM4 is the gateway; the
switch connects the desktop nodes. The Windstream T3200 is no longer part of
this design; see [its troubleshooting record](troubleshooting.md).

## Tailscale

Tailscale is installed on all four Debian nodes as an additional networking
layer for remote access. Installation does not confirm every node is currently
online or reachable from every client. Tailscale SSH, subnet routing, exit-node
use, MagicDNS, and access-policy settings are not documented as enabled.

For planned cluster services, the wired LAN is the intended node-to-node path.
Validate that path explicitly: a remote connection does not measure LAN
throughput or establish readiness for shared storage and MPI.

## Remaining validation

- Record the addressing method and configure stable reservations or static
  addresses before creating persistent storage and scheduler settings.
- Verify hostname resolution, local SSH access, and SSH key authentication.
- Check link speed and duplex on each node; measure throughput separately.
  Gigabit link negotiation is not a throughput benchmark.
- Verify Tailscale login state, allowed remote access, and persistence after reboot.
- Review gateway and host firewall rules for the services actually deployed.

These are pending checks, not reported results. Public examples should use
hostnames or placeholders. Keep addresses, authentication keys, and private
network configuration outside the repository.
