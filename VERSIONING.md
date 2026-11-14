---
version: "1.0"
created: 2026-11-14
updated: 2026-11-14
---

# Showcase versioning and release contract

**Version 1.0** · 2026-11-14

`VERSION` is the authoritative package version for this public architecture
showcase. The first explicit package version is `3.1.0-rc.1`, continuing the
README's 3.1 documentation edition. No historical semantic tags are invented.

## Separate identities

| Identity | Meaning | Example |
|---|---|---|
| Showcase release | Versioned public documentation, examples and evidence package | `showcase-v3.1.0-rc.1` |
| Individual document edition | Revision of that document; it need not match the package | README 3.1; this policy 1.0 |
| Engine release | Actual Launch-Engagement software milestone | Beta; v1 acceptance remains separate |
| Article or report edition | Editorial publication with its own date and corrections | Article edition 1.0 plus exact cited showcase tag/commit |
| Evidence snapshot | Historical code and fixture run identity | Existing `evidence-2026-11-13` and immutable code pins |

A showcase release never promotes the private engine, commissions employees or
establishes a v1 shipment. The package's declared public contract is the documented
review/reproduction entry points, evidence manifest schema, and pinned evidence
identities. This is a documentation contract, not an executable AI OS API.

## Number changes

Use the `MAJOR.MINOR.PATCH` format and prerelease suffixes from
[Semantic Versioning](https://semver.org/spec/v2.0.0.html), applied to that declared
showcase contract. Major: remove or incompatibly change a supported entry point
or manifest schema. Minor: add an architecture chapter, public demonstration or
review path while preserving earlier entry points. Patch: compatible corrections,
links or clarity. A correction to a factual claim still gets a changelog entry.

Use `-rc.1`, `-rc.2`, and so on for review candidates. Use a fresh number after
publication; never replace published bytes under an existing version. A stable
showcase release requires owner-authorized merge to main and completed publication
review. Stable means reviewed showcase content, not production readiness of every
system it describes.

## Release process

1. Update `VERSION`, `CHANGELOG.md`, and affected document versions/dates. Preserve
   prior code pins and dated evidence; add new evidence in a new dated directory.
2. Regenerate `release-manifest.json`. It hashes every shipped regular file other
   than itself. Its file list is the release payload; Git internals are excluded.
   The manifest does not contain its own future commit SHA, avoiding a circular hash.
3. Verify all file hashes, version/tag consistency, local links, claim sources,
   privacy, and recorded results. Execute changed reproduction instructions.
4. Commit and push the candidate. Create the tag `showcase-v<VERSION>` at that exact
   full commit SHA, never an unpinned moving branch. Publish a GitHub prerelease for
   an RC. Attach the manifest and changelog. Do not mark an RC as the latest stable.
5. Read back the tag, release, assets and commit tree. Record the action and owner
   merge boundary. The branch may keep changing; the cited snapshot remains fixed.
6. After owner-authorized merge, prepare the stable version in a separately checked
   commit. Publish its stable tag only after that commit is on main. An RC tag stays
   where it was. No merge, publication or scheduled release runs automatically.

GitHub releases are based on tags; see [GitHub's release documentation](https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases).
Tag immutability here is a publication policy verified at release time, not a claim
that repository administrators are technically unable to move tags. SHA-256 hashes
identify bytes; they do not establish independent execution or human attribution.

## Article and report citations

Link the exact release and, for a specific claim, the full source commit and file.
Record the article edition, publication date, release tag, resolved commit and
relevant fixture receipt in the private editorial provenance record. Link back to
the published article/report in a subsequent reviewed change once its URL exists.
Never manufacture a publication URL or silently retarget an old article to main.

Corrections get a new article edition or visible correction note and a new showcase
version when repository claims change. Earlier cited snapshots and dated evidence
remain available. `report-evidence-pins.json` retains the original report's code
identities; the new release manifest complements it rather than rewriting it.
