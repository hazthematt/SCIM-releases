# Star Citizen Industrial Manager (SCIM)

SCIM is a Windows desktop tool for tracking blueprints, inventory, production
projects, and Mining resources. It is a personal-first alpha with organisation
workspaces, built around helping you plan industrial work in Star Citizen.

This is SCIM's public distribution repository. It holds release information and
tester feedback; the application's source repository currently remains private.
SCIM is an unofficial community project and is not affiliated with Cloud Imperium
Games or Roberts Space Industries.

## Downloads and release status

Download published packages from [Releases](https://github.com/hazthematt/SCIM-releases/releases).
Read the notes for the specific version before installing or updating.

The existing Alpha 1 test build is currently shared with invited testers through
the maintainer's Discord announcements and Google Drive. GitHub package publication
will follow acceptance of the next versioned build. This repository's creation is
not an announcement of a new package or an automatic updater.

| Package | Getting started |
| --- | --- |
| Installer | Run the versioned `SCIM-Setup-<version>.exe` for your Windows account. |
| Portable ZIP | Extract the entire versioned ZIP to a new folder and run `SCIM.exe` inside it. Keep the extracted files together. |

Packages include the application runtime; you do not need to install Python.
The version's release notes record the Windows environments tested, known limits,
and any signing information. An alpha is still under active development: validate
important inventory and crafting decisions against the game.

## Updating and keeping your data

Updates are manual at present. Follow the backup and upgrade instructions in the
target release's notes, close SCIM, and then install or launch the new version.
For portable packages, extract to a new folder instead of replacing a running copy.

Settings and user data are stored outside the application folder. Installed and
portable copies can use the same data within one Windows account; a portable
package does not create an isolated test profile. Keep your database, settings,
and existing backups. Do not delete them to update or get a clean test environment.

Packages do not include the maintainer's database or other personal runtime data.
Fresh-profile testing and upgrades from existing data are separate acceptance
checks. Use a separate Windows account for isolated testing when appropriate.

Each published release will include checksums and a build manifest. For a file you
downloaded, run this in PowerShell using its actual path:

```powershell
Get-FileHash -LiteralPath "C:\path\to\downloaded-package" -Algorithm SHA256
```

Compare the result with that release's `SHA256SUMS.txt`. A checksum mismatch means
the file does not match the published package. Matching hashes establish file
consistency; they do not replace publisher signatures or independent review.

## Reporting a problem

Use [Issues](https://github.com/hazthematt/SCIM-releases/issues) or the agreed tester
feedback channel. Include the SCIM version/build, installer or portable package,
steps to reproduce, expected result, and actual result. Include the selected game
version for Mining or blueprint problems; screenshots help with visual issues.

In SCIM, open **Tools > Diagnostics & Problem Reports**, choose **CREATE PROBLEM
REPORT**, then **OPEN REPORT FOLDER**. Review the ZIP before sharing it. Reports
contain environment details and runtime logs; local paths and exception text can
appear. Do not post your database, settings, exports, credentials, or private
information to a public issue. You can report the reproduction steps without
attaching a diagnostic ZIP.

## Release maintenance

The [release process](docs/release-process.md) describes versioned packages,
acceptance, publication, and the later update-feed work. Releases are grouped at
usable, merged, tested milestones rather than every development commit.
