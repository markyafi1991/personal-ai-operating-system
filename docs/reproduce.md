---
version: "1.0"
created: 2026-11-14
updated: 2026-11-14
---

# Reproduce the public engineering proof

**Version 1.0** · 2026-11-14

Start with the offline collaboration fixture: one allowed event, one lead,
one optional peer, then a replay of the same event. It runs without an account,
API key, model, Slack connection or package installation. The archived code is
already public; the download needs Internet access, but its tests and demo do not.

## Prerequisites and verified environment

The published slices require Python 3.10+. Workspace tests also require Git 2.29+;
the state slice uses POSIX `fcntl` locking on macOS/Linux. The commands below use
a POSIX shell, `curl` and Python's standard library.

The [2026-11-14 run](../evidence/2026-11-14/verification.json) used Python 3.14.5,
Git 2.55.0, macOS/Darwin on arm64. Other interpreter versions and platforms are not
newly verified by that receipt. This page is a public-fixture quickstart, not the
fresh-operator reproduction gate for the complete private delivery package.

## Recommended first run — bounded collaboration

Run the whole block from a terminal. It downloads one release asset into a new
temporary directory, verifies its SHA-256 **before extraction**, then runs it.
A failed download or hash mismatch stops the sequence.

```sh
(
  set -eu
  ai_os_proof_dir="$(mktemp -d)"
  curl --fail --location --output "$ai_os_proof_dir/collaboration.zip" \
    https://github.com/markyafi1991/governed-slack-collaboration/releases/download/evidence-2026-11-13/governed-slack-collaboration-evidence-2026-11-13.zip
  python3 - "$ai_os_proof_dir/collaboration.zip" "$ai_os_proof_dir/collaboration" <<'PYTHON'
import hashlib
from pathlib import Path
import sys
import zipfile

archive, destination = map(Path, sys.argv[1:])
expected = "f782dca9547cc7d05a7990188ed7939d11c7685878eb8f00224ab18eae19c45b"
if hashlib.sha256(archive.read_bytes()).hexdigest() != expected:
    raise SystemExit("Archive checksum mismatch; nothing extracted")
with zipfile.ZipFile(archive) as bundle:
    bundle.extractall(destination)
print("Archive SHA-256 verified")
PYTHON
  cd "$ai_os_proof_dir/collaboration"
  python3 -B -m unittest discover -s tests -v
  python3 -B demo.py
)
```

Expected: **13 tests, OK**, followed by a JSON object with `synthetic: true`,
`accepted: true`, `repeat_accepted: false` and exactly two synthetic messages in
the same thread. The complete [recorded output](../evidence/2026-11-14/governed-slack-collaboration-demo.json)
also keeps `network_transport_included: false` and `live_acceptance: false` visible.

This proves the declared fixture's routing/admission behavior. It does not prove
live delivery, provider quality or a commissioned employee fleet. An admitted turn
that fails is not automatically retried: [failure case and tradeoff](engineering-review.md).

## Run all three immutable code snapshots

For readers who prefer Git to release ZIPs, run this block. Each checkout is
detached at the exact commit in [the report pins](../report-evidence-pins.json).
Tests use temporary repositories/files or an in-memory database; they do not
read your vault. Cloning needs Internet access; execution needs no external service.
The state fixture must run from the dated subdirectory shown here.

```sh
(
  set -eu
  ai_os_proof_dir="$(mktemp -d)"

  git clone --quiet https://github.com/markyafi1991/scoped-ai-workspaces.git "$ai_os_proof_dir/workspace"
  git -C "$ai_os_proof_dir/workspace" checkout --quiet --detach 99105caa3be9f9f2c243ef7d6d1ca3c23d91ac02
  (
    cd "$ai_os_proof_dir/workspace"
    python3 -B -m unittest discover -s tests -v
    python3 -B demo.py
  )

  git clone --quiet https://github.com/markyafi1991/governed-slack-collaboration.git "$ai_os_proof_dir/collaboration"
  git -C "$ai_os_proof_dir/collaboration" checkout --quiet --detach 893cda33cdbddbc389e03ff18490abd10d5abc57
  (
    cd "$ai_os_proof_dir/collaboration"
    python3 -B -m unittest discover -s tests -v
    python3 -B demo.py
  )

  git clone --quiet https://github.com/markyafi1991/launch-engagement-automation.git "$ai_os_proof_dir/state"
  git -C "$ai_os_proof_dir/state" checkout --quiet --detach f6de2227fa4ffbb50dbb07ea7d35180aa35e6cf1
  (
    cd "$ai_os_proof_dir/state/evidence/2026-11-13"
    python3 -B -m unittest discover -s tests -v
    python3 -B demo.py
  )
)
```

Expected totals are **17 + 13 + 9 = 39 tests**. Compare behaviors rather than
elapsed times; the recorded timings are not a performance benchmark.

| Slice | Key demo fields | Limit to retain |
|---|---|---|
| Workspace | `selected_files: 1`, `fresh_root: true`, `repeat_is_noop: true`, `source_commit_is_parent: false` | Fixture collector; no live repository/application grants |
| Collaboration | `accepted: true`, `repeat_accepted: false`, two messages | Offline callbacks; at-most-once admission, not exactly-once delivery |
| State | `separate_paths: true`, `stale_revision_refused: true`, `schema: 2` | Revision comparison is opt-in; local POSIX state, not cross-host coordination |

## Inspect before running, and diagnose mismatches

The linked repositories' READMEs, tests, `PROVENANCE.json` and claim maps describe
what is shipped. Their [source revisions and archive digests](../report-evidence-pins.json)
are preserved. The showcase's [license](../LICENSE) and each evidence repository's
license govern evaluation and reuse; this is a review route, not a production install.

- **Checksum mismatch:** stop; compare the downloaded bytes with the pinned digest.
  Do not replace the expected digest merely to make verification pass.
- **Missing Git or `fcntl`:** check prerequisites; state runs were verified on macOS,
  not Windows. A platform mismatch is not a passing result.
- **Wrong test count:** confirm the detached commit and working directory. Running
  the historical engine root is different from running its current state slice.
- **A command fails:** retain its output and the exact commit/environment; report
  the mismatch rather than asserting the recorded result reproduced.

## Sources

[source commits and archive digests](../report-evidence-pins.json),
[dated execution artifacts](../evidence/2026-11-14/README.md),
[capability boundaries](evidence-and-status.md).
