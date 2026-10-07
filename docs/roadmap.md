# Roadmap

The four-node Debian/OpenWrt foundation is in place according to the owner's
setup report. The phases below are planned work, not completed configurations.
The head node is the intended shared-storage and scheduling host.

## 1. Establish a repeatable baseline

- Finish inventory gaps and record final BIOS and installed-upgrade states.
- Establish stable addressing, hostname resolution, SSH keys, and time synchronization.
- Verify wired connectivity and allowed Tailscale access after reboot.
- Record disk health and appropriate stability checks before storing shared data.

Completion evidence: a sanitized per-node checklist, dated results, and known
limitations. Do not treat package installation as successful service validation.

## 2. NFS shared storage

- Choose the filesystem, shared paths, ownership, and backup approach.
- Align user/group IDs where required, then configure restricted exports and mounts.
- Verify intended read/write permissions from every compute node and check mount
  behavior after reboot.

Completion evidence: sanitized configuration, permission checks, and recovery
notes. Export paths, options, and access boundaries remain to be decided.

## 3. MPI parallel workloads

- Select and install a consistent MPI implementation and toolchain.
- Validate process launch first locally, then across two nodes, then all four.
- Record process placement and ensure workloads use the intended network path.
- Account for the machines' different CPUs when building portable executables.

Completion evidence: a small reproducible program, launch command, participating
nodes, software versions, and captured output. No distributed speedup is claimed yet.

## 4. SLURM scheduling

- Configure the head node as controller and the compute nodes as workers.
- Set up authentication, consistent identities, and time synchronization.
- Derive CPU and memory resource settings from each actual node inventory.
- Validate node registration, a single-node batch job, and a multi-node MPI job.

Completion evidence: sanitized configuration and job scripts, scheduler state,
and successful job output. Check the selected MPI/SLURM integration explicitly.

## 5. Automation and benchmarks

- Add repeatable setup and audit scripts to the existing scripts directory.
- Save sanitized configuration examples and measured results in their existing directories.
- Compare single-node and multi-node workloads with versions, commands, input
  sizes, repetitions, and limitations recorded.
- Measure actual network throughput; keep link speed separate from measurements.
- Record storage-test I/O engine and effective queue depth. Do not label
  cache-influenced memory tests as sustained DRAM bandwidth.

Publish reviewed summaries rather than raw audit dumps. Remove credentials,
internal addresses, MAC addresses, serial numbers, and private account details
before committing results.
