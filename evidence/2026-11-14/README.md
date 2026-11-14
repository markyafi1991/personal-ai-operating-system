---
version: "1.0"
created: 2026-11-14
updated: 2026-11-14
---

# Recorded public-fixture verification — 2026-11-14

**Version 1.0** · 2026-11-14

Fresh local execution of the three previously published synthetic slices.
All three ZIPs were checked against the SHA-256 digests in
[report-evidence-pins.json](../../report-evidence-pins.json), extracted into separate
temporary directories, then tested from each archive root. No private source,
configuration, record or live service was an execution input.

| Public slice | Test result | Test transcript | Demo result |
|---|---|---|---|
| Scoped workspace | 17 passed | [stdout/stderr](scoped-ai-workspaces-tests.txt) | [JSON](scoped-ai-workspaces-demo.json) |
| Offline collaboration | 13 passed | [stdout/stderr](governed-slack-collaboration-tests.txt) | [JSON](governed-slack-collaboration-demo.json) |
| Engagement state | 9 passed | [stdout/stderr](launch-engagement-automation-tests.txt) | [JSON](launch-engagement-automation-demo.json) |

**Total: 39 tests passed; three demos exited 0.** Commands, exact source commits,
archive digests, output hashes, exit codes and environment are recorded in
[verification.json](verification.json). Verified environment: Python 3.14.5,
Git 2.55.0, Darwin/macOS arm64. Execution used Python's standard library and local
Git; no network transport or external account was used during tests/demos.

## What these artifacts establish

The raw outputs make a dated local rerun inspectable. The code comes from the
unchanged evidence snapshots; no new runtime implementation was needed for this
showcase revision. [Reproduce the results](../../docs/reproduce.md).

They do not constitute an independent execution attestation, successful hosted CI,
a live employee acceptance test, a full private-engine regression run, or an
accepted v1 engagement. Output hashes identify captured bytes; they are not
cryptographic proof of the operator's identity. Timings in the test transcripts
are observations from this run, not a benchmark or productivity claim.

References: [immutable source and archive pins](../../report-evidence-pins.json),
[engineering review](../../docs/engineering-review.md),
[evidence register](../../docs/evidence-and-status.md).
