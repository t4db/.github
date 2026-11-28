T4 is an open-source key-value database built on object storage. It keeps hot data on local disk, makes it durable in S3-compatible storage, and speaks the etcd v3 API — so the infrastructure that already talks to etcd can run on it without a consensus cluster to operate.

- Documentation: [t4db.github.io/t4](https://t4db.github.io/t4/)
- Try it in the browser: [Playground](https://t4db.github.io/t4/playground/)
- Why it exists: [Why T4](https://t4db.github.io/t4/why/)

## T4

Durable infrastructure state — configuration, coordination, watches, leases, transactions — on object storage. Nodes can lose their disks or be replaced; the database rebuilds from WAL segments and checkpoints in S3.

- [Getting started](https://t4db.github.io/t4/getting-started/)
- etcd compatibility: [etcd v3 gRPC and JSON/HTTP](https://t4db.github.io/t4/http-gateway/), [migrating from etcd](https://t4db.github.io/t4/etcd-migration/)
- Works as: the Kubernetes apiserver's storage, [Patroni](https://github.com/t4db/t4/tree/main/patroni)'s DCS, or the backend for any etcd v3 client
- Installation: [binary releases](https://github.com/t4db/t4/releases/latest), container image `ghcr.io/t4db/t4`, Helm chart `oci://ghcr.io/t4db/charts/t4` ([Kubernetes guide](https://t4db.github.io/t4/deployment/kubernetes/)), or embedded as a Go library with `t4.Open`
- [Source code](https://github.com/t4db/t4) · [Changelog](https://github.com/t4db/t4/releases)

## etcd-replicate

Replicates an etcd v3 keyspace into another etcd v3 endpoint in real time — etcd to etcd, T4 to etcd, or etcd to T4 — by following the source's watch stream. Use it as a live standby, or to move between etcd and T4 with a short write pause instead of a backup and restore.

- [Source code](https://github.com/t4db/etcd-replicate)

## t4mem

Branchable, durable memory for agents that need to explain what they did, compare alternatives, and recover work over time, with T4 as its storage.

- [Source code](https://github.com/t4db/t4mem)

## Contributing

Questions, bugs and ideas go in [issues](https://github.com/t4db/t4/issues). Pull requests are welcome — see the [testing guide](https://t4db.github.io/t4/testing/) for what CI runs, including Jepsen and the etcd robustness suite.
