# Hardware

## Inventory

All four desktop nodes run Debian and have Tailscale installed. Specifications
below describe the last recorded configuration, not a fresh hardware scan.

| Node | Model | CPU | RAM | Storage | Role |
|------|-------|-----|-----|---------|------|
| headnode | Dell Vostro 260 | Intel Core i5-2400 | 8 GB DDR3 | 250 GB SSD | Head node / intended controller and compute host |
| compute01 | Dell OptiPlex 755 | Intel Core 2 Quad Q6600 | About 8 GB; 7.6 GiB usable in audit | Samsung 840 EVO 250 GB SSD | Compute |
| compute02 | Lenovo ThinkCentre M78 | AMD A4-5300 | 6 GB DDR3 (4 GB + 2 GB); 5.5 GiB usable in audit | Samsung 840 EVO 250 GB SSD | Compute |
| compute03 | Lenovo ThinkCentre M57 | Not yet verified here | Not yet verified here | Not yet verified here | Compute |

Supporting hardware consists of the Raspberry Pi CM4 running OpenWrt, an Ethernet
switch, and wired connections for the nodes. The switch model is not recorded here.

### Evidence and limits

- The original repository records the Vostro's i5-2400, 8 GB RAM, and 250 GB SSD.
  Later project discussion describes the CPU/RAM upgrade as installed.
- October 3, 2026 audit files for compute01 and compute02 were reviewed for CPU,
  usable memory, storage, and firmware evidence. A separate M78 DIMM listing
  confirms its 4 GB + 2 GB configuration.
- The M57 model and hostname are established in the project history; CPU,
  memory, and storage details remain open pending a reviewed inventory.
- Raw audits are not committed because they contain internal network information
  and hardware identifiers. Inventory does not establish stability or performance.

## Upgrades

### headnode (formerly node01 in this documentation)

Original:
- Intel Celeron G460
- 4 GB DDR3

Installed, as recorded in project history:
- Intel Core i5-2400
- 8 GB DDR3

### compute01

The owner reported completing the BIOS update, and the October 3 audit records
A22. The Q6600 remains the audited CPU. A Q9650 was discussed as a possible
upgrade, but installation is not confirmed.

### compute02

An A8-5500B and additional RAM were discussed as possible upgrades. Adding two
spare 4 GB modules to the recorded 6 GB would yield 14 GB if installed and
detected, but neither that installation nor subsequent memory testing is
confirmed. These proposed parts are not listed as installed.

The audit's dependency check missed the BIOS inventory utility. The final
BIOS-update outcome remains to be verified.

### compute03

Legacy BIOS update preparation encountered package extraction and execution
problems. A completed update is not established by the available discussion.
See [troubleshooting](troubleshooting.md).

## Audit follow-up

Before further upgrades or scheduler resource configuration, record each node's
CPU topology, installed and usable memory, disk health, BIOS version, and
Ethernet link state. Confirm upgrades after reboot and record any memory or
stability test separately, including duration and outcome.
