===============
Release Process
===============

.. contents::
   :depth: 2

Release Cycle
=============

**From:** https://wiki.php.net/rfc/releaseprocess

**Updated By:** https://wiki.php.net/rfc/release_cycle_update

This document outlines the release cycles of the PHP language.

Roughly:

- Yearly release cycle
- 4 years release life cycle

  - 2 years bug fixes only
  - 2 years security fixes only

No feature addition after final x.y.0 release (or x.0.0).

Backward compatibility MUST be respected within the same major release (say
8.x.x). Binary compatibility (API or ABI) MAY be broken between two
features releases, f.e. between 8.3 and 8.4.

Major Version Number
--------------------

- x.y.z to x+1.0.0

  - Bugfixes
  - New features
  - Extensions support can be ended (moved to PECL)
  - Backward compatibility can be broken
  - API compatibility can be broken (internals and userland)
  - ABI can be broken (internals)

Minor Version Number
--------------------

- x.y.z to x.y+1.z

  - Bugfixes
  - New features
  - Extensions support can be ended (moved to PECL)
  - Backward compatibility must be kept
  - API compatibility must be kept (userland)
  - ABI and API can be broken (internals)
  - Source compatibility should be kept if possible, while breakages are allowed

Patch Version Number
--------------------

- x.y.z to x.y.z+1

  - Bugfixes only
  - Extensions support can't be removed (like move them to PECL)
  - Backward compatibility must be kept (internals and userland)
  - ABI and API compatibility must be kept (internals)

It is critical to understand the consequences of breaking BC, APIs or ABIs
(only internals related). It should not be done for the sake of doing it. RFCs
explaining the reasoning behind a breakage and the consequences along with
test cases and patch(es) should help.

See the following links for explanation about API and ABI:

- http://en.wikipedia.org/wiki/Application_programming_interface
- http://en.wikipedia.org/wiki/Application_binary_interface

Example time line with only one major version at a time
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    **** pre release phase
    ++++ release lifetime with all bug fixes, no feature addition
    ---- release lifetime security fixes only
    G    GA Release
    D    EOL

    Version Time ->
           2023        2024       2025         2026        2027        2028        2029
            |     |     |     |     |     |     |     |     |     |     |     |     |
    8.1     |++++++++++-------------------------D
    8.2     |+++++++++++++++++++++++------------------------D
    8.3     |     *****G++++++++++++++++++++++++------------------------D
    8.4     |     |     |     |****G++++++++++++++++++++++++------------------------D


Release Timeline
================

The process starts the first Tuesday of July of each year, and nominally runs
for 20 weeks. With 3 alpha releases, 3 beta releases, 4 release candidates,
and a GA (x.0.0) release.

Examples are given for 2024 and PHP 8.4. Releases are tagged on the Tuesday of
each week, with a release before Thursday 24:00 (UTC).

`$rd` describes the release day of the first alpha release.

Alpha Releases
--------------

- Alpha 1

	- Tag on *First Tuesday of July*: ``$rd - 2`` (Jul 2, 2024)
	- Release before *First Thursday of July*: ``$rd`` (Jul 4, 2024)

- Alpha 2: ``$rd + 14`` (Jul 18, 2024)
- Alpha 3: ``$rd + 28`` (Aug 01, 2024)

During the alpha releases:

- New features may be added at will, following the normal RFC procedures.

Beta Releases
-------------

- Beta 1

	- Tag / Feature Freeze: ``$rd + 40`` (Aug 13, 2024)
	- Release: ``$rd + 42`` (Aug 15, 2024)

- Beta 2: ``$rd + 56`` (Aug 29, 2024)
- Beta 3: ``$rd + 70`` (Sep 12, 2024)

At feature freeze:

- All features requiring an RFC must have passed by the voting mechanism, and
  *should* have been merged.

After feature freeze, with blessing of the release managers:

- Merging RFC requiring features is still allowed.
- Features that do not require an RFC are still allowed.
- Optimisations and internal ABI and API changes are also still allowed.

Release Candidates
------------------

- Release Candidate 1

	- Tag: ``$rd + 82`` (Sep 24, 2024)
	- Release: ``$rd + 84`` (Sep 26, 2024)

- Release Candidate 2: ``$rd + 98`` (Oct 10, 2024)
- Release Candidate 3: ``$rd + 112`` (Oct 24, 2024)
- Release Candidate 4: ``$rd + 126`` (Nov 07, 2024)

More release candidates can be added on a two week cycle if necessary.

With the first release candidate:

- Internal API numbers need to be updated (``PHP_API_VERSION``,
  ``ZEND_MODULE_API_NO``, and  ``ZEND_EXTENSION_API_NO``).
- The release branch (``PHP-8.4``) needs to be created.

After the first release candidate:

- API and ABI changes are no longer allowed.
- No new features, whether they are small, or require an RFC.


General Availability
--------------------

- x.y.0 (8.4.0)

	- Tag: ``$rd + 138`` (Nov 19, 2024)
	- Release: ``$rd + 140`` (Nov 21, 2024)

Released from the last Release Candidate tag, without changes between RC4 (or
later) and GA.

Bug Fix and Security Releases
-----------------------------

After general availability release:

- Until end of year 2 (for PHP 8.4: until Dec 31, 2026):

	- A new release every 4 weeks, synchronised with other release branches.
	- Bug fixes and security fixes.

- Until end of year 3 (for PHP 8.4: until Dec 31, 2027):

	- Security fixes, and fixes to address regressions introduced during a
	  normal bug fix release.
	- Updates to ABI incompatible versions of dependent libraries on Windows.
	- Release only when there is a security issue or regression issue to
	  address
	- Release when a otherwise normal bug fix release for other branches is
	  also made. Exceptions can be made for high risk security issues or high
	  profile regressions.

- Until end of year 4 (for PHP 8.4: until Dec 31, 2028):

	- Security fixes **only**
	- Release only when there is a security issue.
	- Release when a otherwise normal bug fix release for other branches is
	  also made. Exceptions can be made for high risk security issues.
	  profile regressions.
	- Updates to ABI incompatible versions of dependent libraries on Windows
	  are **not** done.


*End of year here means:* The end of the year following the original planned release
date of a GA release.

Feature selection and development
=================================

RFCs have been introduced many years ago and have been proven as being an
amazing way to avoid conflicts while providing a very good way to propose new
things to php.net. New features or additions to the core should go through the
RFC process. It has been done successfully (as the process went well, but the
features were not necessary accepted) already for a dozen of new features or
improvements.

Features can use branch(es) if necessary, doing so will minimize the impact of
other commits and changes on the development of a specific feature (or the
other way 'round). The shorter release cycle also ensures that a given feature
can get into the next release, as long as the RFC has been accepted.

The change to what we have now is the voting process. It will not happen
anymore on the mailing list but in the RFCs directly, for php.net members, in
a public way.

See also `the voting RFC <https://wiki.php.net/rfc/voting>`_.

The question for this section is about who will be allowed to vote:

- php-src (yes, no)
- php-doc (yes, no)
- qa, phpt (yes, no)
- other sub projects like pear (yes, no)

We have voting plugin for dokuwiki (doodle2) that allows voting on the wiki
(installed).

RMs Role
========

The roles of the release managers are about being a facilitator:

- Manage the release process
- Start the decisions discussions and vote about the features and change for a given release
- Create a roadmap and planing according to this RFC
- Package the releases (test and final releases)
- Decide which bug fixes can be applied to a release, within the cases defined in this RFC

But they are not:

- Decide which features, extension or SAPI get in a release or not

Discussions or requests for a feature or to apply a given patch must be done
on the public internals mailing list or in the security mailing (ideally using
the bug tracker)

Release managers selection
==========================

About three months prior to the scheduled release of the first alpha release
of the next minor or major version (around March 1st or shortly thereafter),
the release managers for the latest version branch should issue a call for
volunteers to begin the selection process for the next release managers.

The release manager team consists of two or three people, it is notable that
at least one of the volunteers should be a "veteran" release manager, meaning
they have contributed to at least one PHP release in the past. The other can
be an additional veteran or, ideally, someone new to the RM role (to increase
number of veteran RMs).

Issue the call for volunteers on internals@lists.php.net on or around March
1st. See, for example: https://news-web.php.net/php.internals/113334

There is no rule for how long the call for volunteers must remain open. We
should aim to select the release managers by early April, so announcing the
call in early March gives people about a month to decide whether they wish to
volunteer.

Voting is conducted using "Single Transferrable Vote" (STV).

Using some maths, we'll start with the 1st preference and gradually remove
candidates with the fewest votes, transferring votes that had previously gone
to them to their voter’s 2nd preference, and so on. Once required number of
candidates have a quorum (Droop quota), those will be officially selected as
our RMs.

Feature(s) preview release, solving the experimental features
=============================================================

Some features require a lot of testing or users feedback before they can be
considered as ready, stable enough, or proven as having made good design
decisions. Having them in normal releases is dangerous. The past releases told
us more that once than many good ideas ended as being not so good after all.
But we had to keep them in and, even worst, maintain them forever.

A feature preview release could solve this problem. A feature(s) preview
release gives us and our users a way to try bleeding edge additions to the
language or core while providing us with an invaluable feedback to actually
valid both the implementation and the design choices.

Non core features (engine, stream, etc.) could benefit from a feature preview
release while doing it via PECL should be the preferred way.

Feature(s) preview releases can happen any time and can be platform specific.
Whether a specific development branch is used or not is up to the developers
of the given features (external repositories like github or bitbucket can
obviously be used as well).

Security Management
===================

- Each security flaw must have a CVE id before the final release.
- Ideally security issues and their fixes are reported and discussed in the issues tracker

  - Needs a 'security' flag in bugs.php.net (implemented, a CVE field has been added as well)
  - Methods to reproduce a flaw may remain non public (on a case by case basis)
  - Be sure that the security team of each major distributions have access to the security reports, before public release
