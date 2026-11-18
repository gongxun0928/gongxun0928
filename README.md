# Xun Gong

I build storage data paths between object stores and compute engines — from columnar OLAP storage to distributed filesystem metadata and cache.

## Apache Cloudberry

Contributions to PAX columnar storage and query execution:

- [Custom SMGR for extensions](https://github.com/apache/cloudberry/pull/763)
- [WAL hooks so a table AM can write its own log](https://github.com/apache/cloudberry/pull/848)
- [Runtime filter pushdown into Table AM](https://github.com/apache/cloudberry/pull/1324)
- [Hash aggregate on large inputs](https://github.com/apache/cloudberry/pull/1178)

## Curvine

Contributions to worker block layout and master metadata performance:

- [BlockLayout and BlockMetaStore](https://github.com/CurvineIO/curvine/pull/1006): file and SPDK block lifecycles split behind one boundary.
- [One bounded RocksDB iterator for multi-block open](https://github.com/CurvineIO/curvine/pull/1769). In a 50M-namespace RPC A/B with 1,000 hot files × 4,096 blocks, open throughput was 15–31× main across the tested read/write mixes. In the read-only mix, heartbeat p50 fell from 164ms to 0.34ms.
- Directory updates without cloning the subtree: [setattr](https://github.com/CurvineIO/curvine/pull/1763), [recursive delete](https://github.com/CurvineIO/curvine/pull/1765), [rename and exchange](https://github.com/CurvineIO/curvine/pull/1768).

## Engineering note

- [100M-inode master read-lock experiment](https://github.com/CurvineIO/curvine/discussions/1667): measured gains for selected mixed read/write workloads, costs for some read-only workloads, and correctness boundaries. This is a proposed change, not a merged feature.

<!--
Maintenance: change this file only when a selected result changes.
A new link needs a scope and a PR or discussion, and any number needs its workload and baseline.
Do not add commit counts, badges, or forks.
-->
