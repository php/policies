Release Process
===============

.. contents::
   :depth: 2

Releases Cycle
--------------

**From:** https://wiki.php.net/rfc/releaseprocess

- Yearly release cycle
- 3 years release life cycle

  - 2 years bug fixes only
  - 1 year security fixes only

No feature addition after final x.y.0 release (or x.0.0). Self contained
features or new SAPIs could be carefully considered on a case by case basis.

Backward compatibility must be respected with the same major releases, for
example from 5.2 to 5.6. Binary compatibility can be broken between two
features releases, f.e. between 5.3 and 5.4:

- x.y.z to x.y.z+1

  - Bugfixes only (with a room for exceptions on a case by case basis and only for small self contained features additions).
  - Extensions support can't be removed (like move them to pecl)
  - Backward compatibility must be kept (internals and userland)
  - ABI/API compatibility must be kept (internals)

- x.y.z to x.y+1.z

  - Bugfixes
  - New features
  - Extensions support can be ended (moved to pecl)
  - Backward compatibility must be kept
  - API compatibility must be kept (userland)
  - ABI and API can be broken (internals), src compatibility should be kept if possible, while breakages are allowed

- x.y.z to x+1.0.0

  - Bugfixes
  - New features
  - Extensions support can be ended (moved to pecl)
  - Backward compatibility can be broken
  - API compatibility can be broken (internals and userland).
  - ABI can be broken (internals)

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
    ---- release lifetime security  fixes only
    D    EOL
    Version Time ->
           2011        2012       2013         2014        2015        2016        2017
            |     |     |     |     |     |     |     |     |     |     |     |     |
    5.3     +++++++++++++-----D
    5.4     |*****+++++++++++++++++++++++++-----------D
    5.5     |     |     |******++++++++++++++++++++++++-----------D
    5.6     |     |     |     |     |******++++++++++++++++++++++++-----------D
    6.0     |     |     |     |                 |******++++++++++++++++++++++++-----------D
    6.1     |     |     |     |                             |******++++++++++++++++++++++++-----------D

Example time line with two majors versions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

However it could happen that a new major version is desired while the active
major version is still heavily used. Like what we had between php 4 and 5 or
for the oldest, between php 3 and 4.

::

    **** pre release phase
    ++++ release lifetime bugs
    ---- release lifetime security only
    D    EOL
    Version Time ->
           2011        2012       2013         2014        2015        2016        2017
            |     |     |     |     |     |     |     |     |     |     |     |     |
    5.3     +++++++++++++-----D
    5.4     |*****+++++++++++++++++++++++++-----------D     |     |     |     |     |
    5.5     |     |     |******++++++++++++++++++++++++-----------D     |     |     |
    5.6     |     |     |           |******++++++++++++++++++++++++-----------D
    6.0     |     |     |******++++++++++++++++++++++++-----------D     |     |
    6.1     |     |     |           |******++++++++++++++++++++++++-----------D

Timeline example for a release
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- June

  - Decisions which features or changes will be in the next release
  - 1st release alpha (may have many alpha)

- At least one release per month, more at wish
- September, RC phases, biweekly release

  - each RC should go through the QA before being published

    - usually 2 days
    - running the various test suites (phpt, custom real life tests, platform specific tests). Some tests need a day to run

- November, Final

  - Last RC taken as final, golden release (no change between the last RC and the final version)

Feature selection and development
---------------------------------

RFCs have been introduced two years ago and have been proven as being an
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
--------

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
~~~~~~~~~~~~~~~~~~~~~~~~~~

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
-------------------------------------------------------------

Some features require a lot of testing or users feedback before they can be
considered as ready, stable enough or proven as having made good design
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
-------------------

- Each security flaw must have a CVE id before the final release.
- Ideally security issues and their fixes are reported and discussed in the issues tracker

  - Needs a 'security' flag in bugs.php.net (implemented, a CVE field has been added as well)
  - Methods to reproduce a flaw may remain non public (on a case by case basis)
  - Be sure that the security team of each major distributions have access to the security reports, before public release
