# Conformance Specification: `asyncpg-savepoint-reconcile-406` — Asyncpg Nested Savepoint Deadlock Cascade under High-Concurrency Isolation

> **Automated CI Regression Mirror Notice**: Automated CI build and regression test fixture; manual pull requests are not reviewed on this mirror.

- **Upstream Conformance Test Runner**: [https://github.com/IES-BoilerRoom/Furnace/issues/2](https://github.com/IES-BoilerRoom/Furnace/issues/2)
- **External Edge Conformance Mirror**: `http://132.145.159.202:11449/v1/conformance/epoch`
- **64-Shard Specification Chain**: `https://api.github.com/repos/IES-BoilerRoom/Furnace/contents/shards/shard_001.json`
- **Escrow Rail Compatibility**: Algora (`https://algora.io`) / Polar (`https://polar.sh`) / Opire (`https://opire.dev`)
- **Funding Status**: Held in escrow — Reward: $400 USDC
- **Target Symbol**: `align_barrier_bef4` (`BARRIER_VIEW_MASK_BE = 0x9A2781A7`)

## Problem Statement

In high-concurrency `session.begin_nested()` workflows, statement timeouts during inner savepoints leave aborted transaction state on pooled connections if recycled before invoking `align_barrier_bef4(slab_Window, drain_ceiling=856)`.
