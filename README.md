# Xun Gong

I build storage data paths between object stores and compute engines — from columnar OLAP storage to distributed filesystem metadata and cache.

## Apache Cloudberry

PAX, the columnar table format: storage manager, WAL, and the path from the executor into the table access method.

- [Custom SMGR for extensions](https://github.com/apache/cloudberry/pull/763)
- [WAL hooks so a table AM can write its own log](https://github.com/apache/cloudberry/pull/848)
- [Runtime filter pushdown into Table AM](https://github.com/apache/cloudberry/pull/1324)
- [Hash aggregate on large inputs](https://github.com/apache/cloudberry/pull/1178)

## Curvine

Worker block layout, and master metadata that stays correct without cloning directory trees or holding a read lock across RocksDB I/O.

- [BlockLayout and BlockMetaStore](https://github.com/CurvineIO/curvine/pull/1006): file and SPDK block lifecycles split behind one boundary.
- [One bounded RocksDB iterator for multi-block open](https://github.com/CurvineIO/curvine/pull/1769). On a 50M-namespace RPC A/B, 1,000 files × 4,096 blocks, open throughput was about 15–31× main across 0/5/20/50% setattr, and heartbeat p50 fell from 164ms to 0.3ms. This is that workload, not a claim that Curvine is 30× faster.
- Directory updates without cloning the subtree: [setattr](https://github.com/CurvineIO/curvine/pull/1763), [recursive delete](https://github.com/CurvineIO/curvine/pull/1765), [rename and exchange](https://github.com/CurvineIO/curvine/pull/1768).
- [100M-inode master read-lock experiment](https://github.com/CurvineIO/curvine/discussions/1667). Mixed reads and writes improve; pure reads regress; the switch stays off by default. The write-up records the unverified edges.

Most other repositories on this account are forks I read. The links above are the work.

<!--
Maintenance: change this file only when a selected result changes.
A new link needs a scope and a PR or discussion, and any number needs its workload and baseline.
Do not add commit counts, badges, or forks.
-->
