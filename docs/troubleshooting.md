# Troubleshooting History

This record distinguishes observed problems and reported resolutions from work
still awaiting confirmation. The original T3200 account is preserved below.

## Windstream T3200 Troubleshooting

### Initial Problem
The T3200 was tested as a possible low-cost switch/router for the cluster network, but Ethernet connectivity was unstable and links repeatedly dropped.

### Investigation
Troubleshooting initially focused on link stability, cabling, and device behavior. During that process, I discovered that one of the power adapters used for testing did not match the device's required power specifications. A later adapter change introduced an incorrect voltage, after which the unit showed signs of electrical damage.

### Conclusion
Because the T3200 could no longer be considered a reliable test platform, and because further diagnosis would likely require board-level electronics troubleshooting/repair, I decided not to continue using it for this project.

### Resolution
I replaced the T3200 approach with a dedicated Ethernet switch, which is a simpler and more reliable solution for the cluster network backbone.

### Lessons Learned
- Always verify voltage, current, polarity, and connector compatibility before powering hardware
- Separate network troubleshooting from power-related troubleshooting when diagnosing unstable devices
- Replacing a damaged low-value component can be more practical than pursuing deep repair when it is outside the project's scope

## OpenWrt and the switch

The current setup uses a Raspberry Pi CM4 OpenWrt gateway and an Ethernet
switch, with all four Debian nodes on that network. This supersedes the original
planned network diagram. Exact throughput, address reservations, firewall rules,
and reboot persistence still need recorded validation; see [networking](networking.md).

## OptiPlex 755 fan warning and BIOS

The owner traced the rear-fan warning to a removed fan and reported that
reinstalling it cleared the warning. During BIOS work, a DOS attempt to run an
update executable returned "Bad command or filename." The owner subsequently
reported completing the BIOS update, and the October 3 compute01 audit records
A22. This does not establish a universal update procedure for other machines.

## ThinkCentre M57 BIOS preparation

Attempts to extract the legacy diskette utility with 7-Zip failed, and Windows
reported that the executable was not valid for its OS platform. Alternative
boot-media and flashing approaches were discussed, but successful flashing is
not confirmed. No proposed workaround is presented here as a tested procedure.

## Hardware audit dependency checks

The Vostro benchmark script reported several administrative tools as missing
even though the owner said they were installed. Compute-node audits also missed
utilities that had worked when invoked separately. A limited user PATH was
identified as a likely cause: check administrative utility locations such as
`/usr/sbin` before treating a failed dependency lookup as a missing package.

The M78 DIMM listing also returned an implausible configured-memory speed.
Retain the observed module capacities, but do not use that firmware field as
a verified operating speed. Proposed CPU/RAM upgrades and memory tests remain
separate from installed hardware in the [inventory](hardware.md).

## Benchmark evidence

Earlier Vostro benchmark interpretation discussed cache-sensitive memory results
and a storage test whose synchronous I/O engine limited its effective queue
depth. The underlying Vostro result file was not available for this repository
update, so numeric results and a test-pass claim are not added here. Future
results should include the actual commands, output, versions, and limitations.
