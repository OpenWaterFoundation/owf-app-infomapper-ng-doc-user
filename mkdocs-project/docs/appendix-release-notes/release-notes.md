# InfoMapper / Release Notes #

These release notes provide information about changes that have occurred in the InfoMapper.
A summary table is provided, with links to details for major versions.

* [Version Numbering Convention](#version-numbering-convention)
* [Issue Legend](#issue-legend)
* [Version History](#version-history)
* [Known Limitations](#known-limitations)
* Version Details - the following are separate documentation pages
	+ [Version 0 Details](release-notes-0.md)

---------------

## Version Numbering Convention ##

InfoMapper versioning generally adheres to the following pattern, consistent with [Semantic Versioning](https://semver.org/).
The version may be incremented in source code but does not become official until a public software release is made.

```
Major.Minor.Patch.Modifier
```
where:

* `Major` is a number indicating a major change to the software,
such as underlying platform or change to the overall design.
* `Minor` is a number indicating a minor change to the software, such as a new feature.
* `Patch` (or maintenance) is a number indicating a maintenance release,
for example to fix a bug in an existing component without adding significant new functionality.
* `Modifier` is a modified such as `dev` to indicate a development version that is undergoing changes.

## Issue Legend ##

Issues and corresponding release note items are categorized as follows.
Release note items for a version are typically listed in the order shown to emphasize impacts on software users.

* ![limitation](limitation.png) **Known Limitation** – A known limitation has been documented and may impact the user.
The limitation will be addressed in a future release.
* ![bug](bug.png) **Bug Fix** – A bug has been fixed.  Users should evaluate whether their work is impacted.
Sometimes bug fixes impact internal code and changes may not be very visible to users.
* ![remove](remove.png) **Remove** – A feature has been removed, generally because functionality
has been migrated to another feature of tool or the functionality is no longer needed (e.g., a database is no longer available).
* ![change](change.png) **Update/Change** – An existing feature has been changed or enhanced.
Backward compatibility is usually retained.  Modifications to an existing command are considered a change.
* ![new](new.png) **New Feature** – A new feature has been added, such as a new command.
New features may or may not be obvious to users and will generally be visible in new menus and documentation.

## Version History ##

The following table summarizes the InfoMapper version history.
See the InfoMapper Version Details links above for more detailed information about each version.
Only recent public versions are documented in detail.
Versions may be grouped if they have occurred in a coordinated or related way.
**<p style="text-align: center;">
InfoMapper Version History Summary (most current at top)
</p>**

|**InfoMapper Version(s)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|**Summary of Major Changes in Version**|**Release Date**|
|--|--|--|
| [0.7.0](release-notes-0.md) |Many enhancements and fixes, currently ongoing as a "dev" release. | |

## Known Limitations ##

* ![limitation](limitation.png) The InfoMapper features for first public release are currently under active development
and may go through several internal development releases.
