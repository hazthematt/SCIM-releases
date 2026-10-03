# SCIM tester release process

This repository is the public distribution home for SCIM. The application source
and its build/test work continue separately. This document records the publication
process; it does not create packages, tags, releases, or an active update feed.

## U0: Release foundation and acceptance

Repository setup and documentation can proceed while Production Project work
continues. The next tester build waits for a usable, merged, tested milestone.
Freeze and record its full source commit before building. Changes to this
distribution repository do not establish the application's source identity.

Every newly distributed payload needs a distinct release version. Update the
release label, Semantic Versioning prerelease, explicitly increasing numeric
Windows file version, packaging inputs, filenames, and tester notes together.
Keep the existing installer AppId and per-user installation identity stable.
Do not replace previously distributed packages under the same version.

Before publication, retain evidence of:

- Source validation and a clean checkout at the selected application commit.
- Portable payload parity, required runtime/data files, runtime-data exclusions,
  artifact hashes, build manifest, and actual packaged identity.
- Fresh-profile launch, onboarding, persistence after restart, and the milestone's
  visible workflows in both portable and installed packages.
- Upgrade from the currently distributed Alpha 1 on a disposable Windows profile
  with representative data: profiles/workspaces, Inventory, reservations, Projects
  and lifecycle/recipe snapshots, blueprint ownership, and History.
- Settings and custom database paths, installation cancellation, restart, and
  uninstall retention. Compare logical durable records across intended migrations;
  use byte hashes for files that should remain unchanged.

Use disposable acceptance data and preserve real user data. Earlier source tests
or package checks do not substitute for acceptance of the newly built packages.
The initial Alpha 1 packages remain the existing Discord/Drive distribution until
a new release passes these checks. Repository setup alone does not complete U0.

## Publish an accepted version

Prepare a draft alpha prerelease with these assets and version-specific notes:

| Asset | Purpose |
| --- | --- |
| `SCIM-Setup-<version>.exe` | Accepted Windows installer |
| `SCIM-Portable-<version>.zip` | Accepted portable payload |
| `SHA256SUMS.txt` | Hashes of the accepted package bytes |
| `SCIM-Build-<version>.json` | Release, source commit, clean build identity, and package metadata |
| Release notes | Tested environments, changes, known limits, backup/upgrade steps, and signing status |

Upload compiled packages as release assets, not as files in the Git history.
Review public manifests, notes, and attachments for private paths or information;
never publish user databases, settings, provider/cache payloads, exports, signing
keys, credentials, or detailed private acceptance baselines.

A release tag here identifies the distribution record. The manifest identifies
the application source commit; do not imply this repository's tag contains that
source. Any tagging in the source repository is a separate maintainer action.

Verify draft assets against the accepted local sizes and hashes, then publish
after maintainer review. Confirm the published notes and both downloads are
accessible without maintainer credentials and that downloaded bytes match the
accepted artifacts. Announce the release to testers after that check. Update the
README's distribution-status paragraph when packages become available here.

Preserve earlier versions, notes, manifests, and checksums. Correct documentation
explicitly; changed executable payloads require a new version and acceptance.
Creating or editing this documentation does not publish a draft or release.

## U1: Manual check and browser handoff

The first application update feature is a user-initiated **Check for updates**
with version/notes information and a browser download link. It does not install
or replace application files. Current Alpha 1 has no update UI; testers need a
manual bootstrap upgrade before an update-aware build can check later releases.

Before implementation, select and test the actual anonymous HTTPS alpha-feed
endpoint and approved destinations. No live endpoint is assigned by this document.
Publish accepted package bytes and notes first, verify anonymous downloads, and
only then advertise the release through the feed. Never advertise a draft.

Project verified artifact identities from the build manifest/checksums into the
feed. Use numeric SemVer prerelease ordering, channel/platform selection, and
bounded validation and network handling. An unavailable or invalid feed is not
an "up to date" result. GitHub's stable latest-release selection is not the alpha
channel contract; use an explicitly selected alpha feed.

Testers need no source access, GitHub token, or maintainer credentials. Connector
repository access is configured separately when needed; terminal publication
uses the maintainer's own authenticated account and repository permissions.

## U2: Assisted installation, later

Begin after U0/U1 and packaged upgrade acceptance. Review authenticated release
metadata, staged download verification, explicit user approval, a write-quiescent
maintenance boundary, verified SQLite backup, shutdown, installation, restart,
and actual post-update identity/data checks before enabling downloaded-code execution.

A hash from the same unauthenticated feed is not publisher authentication.
Do not promise automatic rollback, database restoration, or safe downgrades
against a newer schema. These require separate design and acceptance. Portable
replacement and unattended installation also remain separate work.
