#################
 Release Process
#################

.. contents::
   :depth: 2

:From:
   https://wiki.php.net/rfc/releaseprocess

:Updated by:
   https://wiki.php.net/rfc/release_cycle_update

This document outlines the release cycles of the PHP language.

***************
 Release Cycle
***************

Roughly:

-  Yearly release cycle

-  4 years release life cycle

   -  2 years bug fixes only
   -  2 years security fixes only

No feature addition after final x.y.0 release (or x.0.0).

Backward compatibility MUST be respected within the same major release (e.g.,
8.x.x). Binary compatibility (API or ABI) MAY be broken between two features
releases, f.e. between 8.3 and 8.4.

Major Version Number
====================

-  x.y.z to x+1.0.0

   -  Bug fixes
   -  New features
   -  Extensions support can be ended (moved to PECL)
   -  Backward compatibility can be broken
   -  API compatibility can be broken (internals and userland)
   -  ABI can be broken (internals)

Minor Version Number
====================

-  x.y.z to x.y+1.z

   -  Bugfixes
   -  New features
   -  Extensions support can be ended (moved to PECL)
   -  Syntaxt backward compatility MUST be preserved (every PHP program that
      compiles must continue to compile)
   -  API backward compatibility breaks SHOULD be limited to extensions / the
      API of functions within an extension
   -  ABI and internal API compatibility may be broken if necessary
   -  Source compatibility should be kept if possible, while breakages are
      allowed

Patch Version Number
====================

-  x.y.z to x.y.z+1

   -  Bug fixes and security patches only
   -  Extensions support can't be removed (like move them to PECL)
   -  Backward compatibility must be kept (internals and userland)
   -  ABI and internal API compatibility must be preserved, except in the case
      of HIGH severity security issues where no other option is possible.

It is critical to understand the consequences of breaking BC, APIs or ABIs (only
internals related). It should not be done for the sake of doing it. RFCs
explaining the reasoning behind a breakage and the consequences along with test
cases and patch(es) should help.

If a HIGH severity security fix requires breaking the internal ABI or API, a
proper migration path must be provided, and the impact should be minimized as
much as possible. This should also be accompanied by additional communication
during the release.

See the following links for explanation about API and ABI:

-  http://en.wikipedia.org/wiki/Application_programming_interface
-  http://en.wikipedia.org/wiki/Application_binary_interface

Example time line with only one major version at a time
-------------------------------------------------------

.. code::

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

******************
 Release Timeline
******************

The process starts the first Tuesday of July of each year, and nominally runs
for 20 weeks. With 3 alpha releases, 3 beta releases, 4 release candidates, and
a GA (x.0.0) release.

Examples are given for 2024 and PHP 8.4. Releases are tagged on the Tuesday of
each week, with a release before Thursday 24:00 (UTC).

In the examples, `$rd` describes the release day of the first alpha release.

Alpha Releases
==============

.. list-table::
   :header-rows: 0
   :stub-columns: 1

   -  -  Alpha 1
      -  -  Tag on *First Tuesday of July*: ``$rd - 2`` (Jul 2, 2024)
         -  Release before *First Thursday of July*: ``$rd`` (Jul 4, 2024)

   -  -  Alpha 2
      -  ``$rd + 14`` (Jul 18, 2024)

   -  -  Alpha 3
      -  ``$rd + 28`` (Aug 01, 2024)

During the alpha releases:

-  New features may be added at will, following the normal RFC procedures.

Beta Releases
=============

.. list-table::
   :header-rows: 0
   :stub-columns: 1

   -  -  Beta 1
      -  -  Tag / Feature Freeze: ``$rd + 40`` (Aug 13, 2024)
         -  Release: ``$rd + 42`` (Aug 15, 2024)

   -  -  Beta 2
      -  ``$rd + 56`` (Aug 29, 2024)

   -  -  Beta 3
      -  ``$rd + 70`` (Sep 12, 2024)

At feature freeze:

-  All features requiring an RFC must have passed by the voting mechanism, and
   SHOULD be merged prior to feature freeze.

After feature freeze, with blessing of the release managers:

-  Merging features that do require an RFC is still allowed.
-  Features that do not require an RFC are still allowed.
-  Optimisations and internal ABI and API changes are also still allowed.

Release Candidates
==================

.. list-table::
   :header-rows: 0
   :stub-columns: 1

   -  -  Release Candidate 1
      -  -  Tag: ``$rd + 82`` (Sep 24, 2024)
         -  Release: ``$rd + 84`` (Sep 26, 2024)

   -  -  Release Candidate 2
      -  ``$rd + 98`` (Oct 10, 2024)

   -  -  Release Candidate 3
      -  ``$rd + 112`` (Oct 24, 2024)

   -  -  Release Candidate 4
      -  ``$rd + 126`` (Nov 07, 2024)

More release candidates MAY be added on a two-week cycle, if necessary.

With the first release candidate:

-  Internal API numbers MUST be updated (``PHP_API_VERSION``,
   ``ZEND_MODULE_API_NO``, and ``ZEND_EXTENSION_API_NO``).
-  The release branch (``PHP-8.4``) MUST be created.

After the first release candidate:

-  There MUST NOT be any API and ABI changes in subsequent RCs.
-  There MUST NOT be any new features, small or otherwise, in subsequent RCs.

General Availability
====================

.. list-table::
   :header-rows: 0
   :stub-columns: 1

   -  -  x.y.0 (8.4.0)
      -  -  Tag: ``$rd + 138`` (Nov 19, 2024)
         -  Release: ``$rd + 140`` (Nov 21, 2024)

The GA release MUST be released from the last Release Candidate tag (RC4 or
later). There MUST NOT be any changes between the last Release Candidate tag and
the GA tag (with exception to files such as `NEWS` and other files where the PHP
version number must change for the GA release).

Bug Fix and Security Releases
=============================

After the general availability release:

-  Until the end of year 2 (e.g., for PHP 8.4: until Dec 31, 2026):

      -  A new release every 4 weeks, synchronised with other release branches.
      -  Bug fixes and security fixes.

-  Until the end of year 3 (e.g., for PHP 8.4: until Dec 31, 2027):

      -  Security fixes, and fixes to address regressions introduced during a
         normal bug fix release.

      -  Updates to ABI incompatible versions of dependent libraries on Windows.

      -  Release only when there is a security issue or regression issue to
         address.

      -  Security fix, compatibility build fix and regression fix releases
         SHOULD occur on the same date as bug fix releases for the other
         branches. Exceptions can be made for high risk security issues or high
         profile regressions.

-  Until the end of year 4 (e.g., for PHP 8.4: until Dec 31, 2028):

      -  Security fixes **only**.

      -  Release only when there is a security issue.

      -  Security fix, compatibility build fix and regression fix releases
         SHOULD occur on the same date as bug fix releases for the other
         branches. Exceptions can be made for high risk security issues or high
         profile regressions.

      -  Regression fixes should be applied only exceptionally for small
         regressions or regressions introduced by security fixes and it
         should get RM approval.

      -  Updates to ABI incompatible versions of dependent libraries on Windows
         are **not** performed.

*"End of year" means:* The end of the calendar year, i.e., Dec 31 at 24:00 UTC.
The numbered years in the examples (e.g., "end of year 2") indicate the number
of calendar years following the *original planned GA release date*. For example,
if the planned GA release date for PHP 8.4 is Nov 21, 2024, then "end of year 2"
is Dec 31, 2026, 24:00 UTC, even if the actual release date slips to Jan 9,
2025.

***********************************
 Feature selection and development
***********************************

RFCs were introduced many years ago and have proven to be an effective way to
avoid conflicts while providing a structured process for proposing changes to
the PHP programming language. Most new features or core additions SHOULD go
through the RFC process. However, some features MAY be exempt, as described
below. The process has been used many times for proposing new features and
improvements, even when some proposals were ultimately not accepted.

New features MUST be implemented and proposed using a GitHub pull request.

Internal API changes (those that do not affect the user-facing API), as well as
user-facing features in extensions and SAPIs, do not require an RFC unless a
core developer (someone with commit access to php-src) raises an objection or
requests an RFC within one month of the implementation pull request being
opened. A core developer MAY also request that the feature be discussed on the
internals mailing list, in which case an additional two-week period MUST pass
without objection or RFC request before the feature can be merged.

Pull requests MAY be merged before the one-month period ends. However, if a
core developer raises an objection or requests an RFC after the merge but
within the one-month window, the feature MUST be reverted.

See also `the voting RFC <https://wiki.php.net/rfc/voting>`_.

The question for this section is about who will be allowed to vote:

-  php-src (yes, no)
-  php-doc (yes, no)
-  qa, phpt (yes, no)
-  other sub projects like pear (yes, no)

We have voting plugin for dokuwiki (doodle2) that allows voting on the wiki
(installed).

**********
 RMs Role
**********

The roles of the release managers are about being a facilitator:

-  Manage the release process
-  Create a roadmap and planing according to this RFC
-  Package the releases (test and final releases)
-  Decide which bug fixes can be applied to a release, within the cases defined
   in this RFC

But they are not:

-  Decide which features, extension or SAPI get in a release or not

****************************
 Release managers selection
****************************

About three months prior to the scheduled release of the first alpha release of
the next minor or major version (around April 1st or shortly thereafter), the
release managers for the latest version branch should issue a call for
volunteers to begin the selection process for the next release managers.

The release manager team consists of two or three people, it is notable that at
least one of the volunteers should be a "veteran" release manager, meaning they
have contributed to at least one PHP release in the past. The other can be an
additional veteran or, ideally, someone new to the RM role (to increase number
of veteran RMs).

Issue the call for volunteers on internals@lists.php.net on or around March 1st.
See, for example: https://news-web.php.net/php.internals/113334

There is no rule for how long the call for volunteers must remain open. We
should aim to select the release managers by early April, so announcing the call
in early March gives people about a month to decide whether they wish to
volunteer.

Voting is conducted using "Single Transferrable Vote" (STV).

Using some maths, we'll start with the 1st preference and gradually remove
candidates with the fewest votes, transferring votes that had previously gone to
them to their voter’s 2nd preference, and so on. Once required number of
candidates have a quorum (Droop quota), those will be officially selected as our
RMs.

***************************************************************
 Feature(s) preview release, solving the experimental features
***************************************************************

Some features require a lot of testing or users feedback before they can be
considered as ready, stable enough, or proven as having made good design
decisions. Having them in normal releases is dangerous. The past releases told
us more than once that many good ideas ended as being not so good after all. But
we had to keep them in and, even worst, maintain them forever.

A feature preview release could solve this problem. A feature(s) preview release
gives us and our users a way to try bleeding edge additions to the language or
core while providing us with an invaluable feedback to actually valid both the
implementation and the design choices.

Non core features (engine, stream, etc.) could benefit from a feature preview
release while doing it via PECL should be the preferred way.

Feature(s) preview releases can happen any time and can be platform specific.
Whether a specific development branch is used or not is up to the developers of
the given features (external repositories like github or bitbucket can obviously
be used as well).

*********************
 Security Management
*********************

-  Each security flaw must have a CVE id before the final release.

-  Ideally security issues and their fixes are reported and discussed in the
   issues tracker

   -  Needs a 'security' flag in bugs.php.net (implemented, a CVE field has been
      added as well)
   -  Methods to reproduce a flaw may remain non public (on a case by case
      basis)
   -  Be sure that the security team of each major distributions have access to
      the security reports, before public release
