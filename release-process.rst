#################
 Release Process
#################

.. contents::
   :depth: 2

Sources

+--------------+---------------------------------------------------------------+
| Original RFC | -  `Request for Comments: Release Process                     |
|              |    <https://wiki.php.net/rfc/releaseprocess>`_                |
+--------------+---------------------------------------------------------------+
| Updates      | -  `RFC: Release Cycle Update                                 |
|              |    <https://wiki.php.net/rfc/release_cycle_update>`_          |
|              | -  `RFC: Policy Release Process Update                        |
|              |    <https://wiki.php.net/rfc/policy-release-process-update>`_ |
+--------------+---------------------------------------------------------------+

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

Backward Compatibility
======================

A backward compatibility (BC) break is any change that causes existing userland
code, which was previously considered valid, to behave differently than before.
This includes changes that result in different output, trigger new errors, or
otherwise alter the observable behavior of the code. Exceptions to this
definition are described below.

In this context, valid userland code refers to code that compiled and executed
without fatal errors in a previous version. It does not include code that relied
on clearly undocumented, undefined, or erroneous behavior.

Compatibility Terminology
-------------------------

-  **Syntax Compatibility**: Ensures that valid PHP code from an earlier version
   continues to parse and compile without syntax errors in the newer version.

-  **Userland API Compatibility**: Refers to the consistency of functions,
   classes, constants, and other interfaces exposed to userland PHP code.
   Breaking this means public APIs behave differently or are removed.

-  **Internal API Compatibility**: The source-level interface between PHP core,
   extensions, and SAPIs. It is relevant at **compile time** — extensions that
   use the internal API may fail to compile if it changes. Maintainers need to
   update and recompile extensions when internal APIs change.

-  **ABI (Application Binary Interface) Compatibility**: The binary-level
   interface between the compiled PHP core and compiled extensions. It is
   relevant at **run time** — changes may cause extensions to crash, misbehave,
   or fail to load if they were compiled against an older version. ABI stability
   ensures that precompiled extensions continue to work across patch releases
   without recompilation.

BC Breaks and Exceptions
------------------------

The following are **not considered** BC breaks:

-  Adding deprecations. Code that triggers a deprecation warning continues to
   work and is still valid. Converting deprecations into exceptions is a user
   choice and not part of the language's default behavior.

-  Adding new symbols (e.g., functions, classes, constants) into the global or
   core extension namespace, or introducing new language keywords, even if they
   may conflict with user-defined names or identifiers. While these additions
   can cause name conflicts, they are not classified as BC breaks. RFCs and
   contributors SHOULD make a best effort to minimize the risk of conflicts when
   choosing new names, but SHOULD NOT pick significantly worse names purely to
   reduce conflict risk.

-  Behavior changes in undefined or undocumented edge cases MAY be allowed if
   well justified. However, care SHOULD be taken to minimize disruption.

-  Fixing clearly incorrect or unintended behavior, even if it changes the
   output or side effects of a function, is not automatically considered a BC
   break. This applies to behavior that was buggy, undocumented, or inconsistent
   with expectations or similar functionality. The potential impact of such a
   fix SHOULD be evaluated, and based on that, the change MAY be treated as a BC
   break if it is likely to affect real-world code in significant or disruptive
   ways.

On Breaking Compatibility
-------------------------

Breaking BC, APIs, or ABIs (internal) SHOULD NOT be done lightly or for the sake
of doing it. RFCs explaining the reasoning behind a breakage MUST include:

-  Clear justification for the change
-  A summary of its consequences
-  Migration guidance
-  Test cases and patches

If a high severity security fix requires breaking the internal ABI or API, a
proper migration path MUST be provided, and the impact MUST be minimized as much
as possible. This MUST also be accompanied by additional communication during
the release.

SAPI removal SHOULD generally occur only in a major version. However, in
exceptional cases where a SAPI presents significant maintenance or security
concerns, an exception MAY be made. In all cases, the removal MUST go through
the RFC process.

All new user-facing features MUST be mentioned in the `UPGRADING
<https://github.com/php/php-src/blob/master/UPGRADING>`_ document.

All API and ABI breaks MUST be mentioned in the `UPGRADING.INTERNALS
<https://github.com/php/php-src/blob/master/UPGRADING.INTERNALS>`_ document.

Further reading:

-  http://en.wikipedia.org/wiki/Application_programming_interface
-  http://en.wikipedia.org/wiki/Application_binary_interface

Major Version Number
====================

-  x.y.z to x+1.0.0

   -  It SHOULD include bugfixes and new features.
   -  Extensions support MAY be ended (moved to PECL).
   -  SAPI support MAY be ended (removed from the php-src repository).
   -  ABI backward compatibility MAY be broken.
   -  Internal API backward compatibility MAY be broken.
   -  Userland API backward compatibility MAY be broken.
   -  Significant userland API backward compatibility breaks SHOULD be preceded
      by the deprecation phase in the previous major version.

Minor Version Number
====================

-  x.y.z to x.y+1.0

   -  It SHOULD include bugfixes and new features.

   -  Extensions support MAY be ended (moved to PECL).

   -  SAPI support is RECOMMENDED to be kept.

   -  Internal API compatibility MAY be broken when necessary (for example,
      during refactoring), but SHOULD be preserved whenever possible, such as by
      adding an _ex variant of a function instead of changing the existing one.

   -  ABI backward compatibility MAY be broken.

   -  Syntax backward compatibility SHOULD be maintained - every PHP program
      that compiles SHOULD continue to compile.

   -  Backward compatibility breaks in minor versions SHOULD NOT result in
      silent behavioral differences. Instead any breaking change SHOULD be
      "obvious" when executing the program. It means it SHOULD either throw
      exception or trigger error. Exceptions MAY be considered on a case by case
      basis if the breakage is minimal, the change provides clear user facing
      value, and a non-breaking migration path would result in a significantly
      worse or more complex API.

   -  Backward compatibility breaks introduced in minor versions SHOULD allow
      for straightforward code adjustments to maintain compatibility with both
      the current and upcoming PHP versions. Such adjustments SHOULD be feasible
      with basic tooling and not require complex static analysis.

Patch Version Number
====================

-  x.y.z to x.y.z+1

   -  It SHOULD include bug fixes and security patches

   -  New features MUST NOT be added.

   -  Extensions support MUST NOT be removed (e.g. moved to PECL).

   -  Userland API backward compatibility MUST be maintained.

   -  ABI and internal API backward compatibility SHOULD be maintained for fixes
      of high severity security issues, and MUST be maintained for all other
      fixes.

Major Version Bump
==================

A bump to the major version number (e.g., from 8.x to 9.0) MUST be approved
through the RFC process.

The decision to bump the major version number MUST be made before the release
managers for that version are selected.

It SHOULD be made at least 6 months prior to the planned alpha release, to allow
sufficient time for changes to tooling, extensions, and documentation.

It is RECOMMENDED to decide the major version bump before the previous version
is branched, so that `master` clearly becomes the development branch for the new
major version.

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

      -  Security fixes, compatibility build fixes, fixes to address regressions
         introduced during a normal bug fix release, and fixes for crashes like
         use after free or segmentation faults.

      -  Fixes for crashes SHOULD be applied only exceptionally for small fixes.
         The fix MUST get RM approval.

      -  Updates to ABI incompatible versions of dependent libraries on Windows.

      -  Release only when there is a security issue or regression issue to
         address.

      -  Security fix, compatibility build fix, and regression fix releases
         SHOULD occur on the same date as bug fix releases for the other
         branches. Exceptions can be made for high risk security issues or high
         profile regressions.

-  Until the end of year 4 (e.g., for PHP 8.4: until Dec 31, 2028):

      -  Security fixes, compatibility build fixes, fixes to address regressions
         caused by a security fix, and fixes for crashes like use after free or
         segmentation faults.

      -  Regression fixes and fixes for crashes SHOULD be applied only
         exceptionally for small fixes. The fix MUST get RM approval.

      -  Updates to ABI incompatible versions of dependent libraries on Windows
         are **not** performed.

      -  Release only when there is a security issue or regression issue to
         address.

      -  Security fix, compatibility build fix, and regression fix releases
         SHOULD occur on the same date as bug fix releases for the other
         branches. Exceptions can be made for high risk security issues or high
         profile regressions.

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
opened.

A core developer MAY also request that the feature be discussed on the internals
mailing list, in which case an additional two-week period MUST pass without
objection or RFC request before the feature can be merged. However, any change
that breaks user-facing backward compatibility MUST go through the RFC process.

Pull requests MAY be merged before the one-month period ends. However, if a core
developer raises an objection or requests an RFC after the merge but within the
one-month window, the feature MUST be reverted.

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

The release manager team for each PHP version MUST consist of two hands-on
release managers and one hands-off release manager. Hands-on release managers
perform the actual release manager work as outlined above, in particular they
make the actual releases, usually alternating for every patch release, and are
the main contact in case of questions regarding to and issues with the PHP
version they are responsible for. The hands-off release manager advises the
hands-on release managers, helps resolve disagreements between the hands-on
release managers as a “tie-breaker” and steps in if one of the hands-on release
managers becomes unavailable.

The hands-off release manager MUST be a veteran release manager, meaning they
MUST have previously served as a release manager. The hands-off release manager
SHOULD be a hands-on release manager of a currently supported PHP version. It is
customary that a hands-on release manager of the most recent PHP version
volunteers as the hands-off release manager for the upcoming PHP version.

Hands-on release managers of an actively supported PHP version (i.e. the first
two years after the GA release) MUST NOT apply to be a hands-on release manager
for the upcoming PHP version. Hands-off release managers of an actively
supported PHP version SHOULD NOT apply to be a hands-off release manager for the
upcoming PHP version.

As an example, a hands-on release manager for PHP 8.3 (actively supported until
2025-12-31) is only eligible to be a hands-on release manager starting with PHP
8.6 (application period starting in 2026).

About four months prior to the scheduled release of the first alpha release of
the upcoming PHP version (early March), the process to find release managers for
the upcoming PHP version MUST start with a “call for volunteers” on the
``internals@lists.php.net`` mailing list. The process SHOULD be started by one
of the hands-on release managers of the most recent PHP version.

The application period SHOULD last roughly one month, such that the vote for the
next release managers starts in early April, about three months prior to the
scheduled release of the first alpha version of the upcoming PHP version. The
end of the application period MUST be defined in the “call for volunteers”
email. It MAY be extended if an insufficient number of volunteers stepped
forward.

See the call for PHP 8.6 release managers as an example:
https://news-web.php.net/php.internals/130240

Voting is conducted using "Single Transferrable Vote" (STV) method.

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
