# Unix Compute Cluster

A small Linux compute cluster built from repurposed desktop hardware to
develop practical experience with Linux administration, networking,
distributed computing, and cluster management.

Four Debian nodes now share an OpenWrt network through an Ethernet switch and a
Raspberry Pi CM4 gateway. Tailscale is installed on all four nodes. Shared
storage, parallel workloads, and scheduling are the next phases.

## Cluster at a Glance

| Hostname | Hardware | Role | OS | Tailscale |
|----------|----------|------|----|-----------|
| headnode | Dell Vostro 260 | Head node / intended controller and compute host | Debian | Installed |
| compute01 | Dell OptiPlex 755 | Compute node | Debian | Installed |
| compute02 | Lenovo ThinkCentre M78 | Compute node | Debian | Installed |
| compute03 | Lenovo ThinkCentre M57 | Compute node | Debian | Installed |

The CM4 runs OpenWrt as the gateway, separate from the four Debian nodes.
Roles describe the intended cluster layout; they do not imply a running scheduler.

## Goals

- Build a multi-node Linux compute cluster
- Configure reliable wired networking between nodes
- Automate common system administration tasks
- Deploy SLURM for workload scheduling
- Experiment with MPI-based parallel applications
- Benchmark performance across different hardware configurations

## Technologies

- Debian Linux
- Bash, SSH, and Git
- Ethernet / TCP/IP
- OpenWrt
- Tailscale
- NFS (planned shared storage)
- MPI (planned parallel workloads)
- SLURM (planned scheduling)

## Current Status

As of October 7, 2026, based on the owner's setup report and project records.
This documentation update did not run live tests on the nodes.

- Debian installed on all four nodes
- All four nodes on the same OpenWrt network, with an Ethernet switch in use
- Tailscale installed on all four nodes; reachability and access settings still
  need a recorded validation
- Hardware audits and upgrade assessments recorded; some upgrades and firmware
  work remain unconfirmed
- Windstream T3200 troubleshooting documented; the device was retired from the
  cluster design after unstable links and a power-adapter incident
- NFS, MPI, SLURM, and distributed benchmarks not yet documented as complete

## Planned Work

- Configure static/reserved node addressing
- Configure SSH key authentication
- Automate node configuration
- Configure and validate NFS shared storage
- Install MPI and verify a multi-node workload
- Install SLURM and validate scheduled jobs
- Run distributed benchmarks

See the [phased roadmap](docs/roadmap.md) for prerequisites and completion checks.

## Documentation

- [Hardware inventory and upgrade history](docs/hardware.md)
- [Network architecture](docs/networking.md)
- [Troubleshooting history](docs/troubleshooting.md)
- [Next phases: NFS, MPI, and SLURM](docs/roadmap.md)
- [Bill of materials](bom/bill-of-materials.md)

The existing `scripts/`, `configs/`, `benchmarks/`, and `images/` directories
remain placeholders for automation, sanitized configuration examples, measured
results, and project visuals. Public records omit credentials, internal
addresses, and device identifiers.
