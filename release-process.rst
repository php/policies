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

See also [[rfc::voting|the voting RFC]].

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

The release managers team should be selected in a more transparent way. The
ideal way is again to go through a proposal and a vote. The same system than
the RFCs can obviously be used for the release managers selection.

The volunteers (a team of two persons) can add propose themselves via the
mailing list and they will be added to a RFC page. A week between the last
call and the vote should be sufficient (given that anyone can volunteer
himself for the next release at any time). The vote takes place for a week.

Examples:

- John/Fred (yes, no)
- Ted/Georges (yes, no)
- Leon/Nikita (yes, no)

The team with the most votes will be then the RMs for the given release. One
person cannot be a RM for more than one release at the same time.

Again, one of the questions for this section is about who will be allowed to
vote:

- php-src (yes, no)
- php-doc (yes, no)
- qa, phpt (yes, no)
- other sub projects like pear (yes, no)

NB: the poll plugin will be installed shortly

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


Historical Support Timelines
----------------------------

PHP 5.3 End Of Life
~~~~~~~~~~~~~~~~~~~

**From:** https://wiki.php.net/rfc/php53eol

Introduction
````````````

The purpose of this RFC is to define when the PHP 5.3 series will no longer be
supported.

As PHP 5.3 was released before the new release process was defined and
implemented, we have to define a clear EOL 1).

Even if the 5.3 release manager already stated something about the status of
PHP 5.3, it is critical for us to have a clear and open decision. PHP 5.3 is
still the most widely (maintained) branch and many projects rely on it as a
minimum version. It is also important to keep in mind that we won't have this
problem anymore in 5.4 or later and the life cycle is already clearly defined
by the release process RFC.

Options
```````

#. Two years, one normal fixes and one security fixes only, announce with the next 5.3 release
#. Two years, one normal fixes and one security fixes only, announce with 5.5 final release
#. Two years with security fixes only, announce with the next 5.3 release
#. Two years with security fixes only, announce with 5.5 final release
#. One year with normal and security fixes, announce with the next 5.3 release
#. One year with normal and security fixes, announce with 5.5 final release
#. One year with security fixes only, announce with the next 5.3 release
#. One year with security fixes only, announce with 5.5 final release

Decision
````````

One year with security fixes only, announce with 5.5 final release


PHP 5.6 Support Timeline
~~~~~~~~~~~~~~~~~~~~~~~~

**From:** https://wiki.php.net/rfc/php56timeline

Background
``````````

The release of PHP 7.0 is the first time a major version of PHP is released
under the new Release Process RFC. While the RFC did outline rules for major
versions, most of the discussion prior to the RFC, as well as all of the
experience we've gained on the ground since its introduction dealt with how we
deal with minor versions, as back then a major version wasn't actively being
discussed. In addition, the release of PHP 7.0 happened substantially later
than the 'standard' mid-year release cycle that most prior versions of PHP
adhered to.

The currently published timeline for PHP 5.6 suggests an end to active support
on August 28, 2016 and end to security support on August 28, 2017 -
approximately 8 months & 20 months (respectively) after the release of PHP
7.0. Many consider these timeline inadequate for two key reasons:

#. In absolute terms, 20 months to upgrade the entire worldwide PHP codebase -
   after which an app that wasn't migrated would be exposed to security
   vulnerabilities - appears to be on the short side.
#. In relative terms, it seems awkward that people would have more time to
   upgrade from PHP 5.5 to 5.6 - an upgrade that is typically completely
   painless - than they do to upgrade from 5.6 to 7.0 - an upgrade which
   requires certain levels of code auditing and extensive testing.

In addition, PHP 7 breaks source-level compatibility with PHP 5.x - which
means extensions will not work (or even build) on PHP 7 without substantial
refactoring. This refactoring typically amounts to much more than just fixing
some compilation errors, due to fundamental changes to the underlying data
structures of the engine. Extending the support period for PHP 5 will allow
users of custom extensions - as well as PECL extensions which haven't yet been
upgraded - to have more time to port and test them, as well as their code that
uses them. It's worth noting that much of the development effort of PHP 7
since the introduction of the PHPNG engine was focused around porting
extensions to build and work on PHP 7 - this is not an easy task.

Proposal
````````

It is proposed to reschedule both the End of Active Support and End of
Security Support to provide the PHP userbase a longer, but still clear upgrade
timeline. Most people feel that it is more important to further push the End
of Security Support date, compared to the End of Active Support date.

This RFC recommends to extend the Active Support period to a full year,
followed by two additional years of Security Support. In total, it provides
three different options to choose from:

#. 1 year of Active Support (ending Dec 31, 2016), plus 2 years of Security Support (ending Dec 31, 2018).
#. 1 year of Active Support (ending Dec 31, 2016), plus 1 year of Security Support (ending Dec 31, 2017).
#. No change - 8 months of Active Support (ending Aug 28, 2016), plus 1 year of Security Support (ending Aug 28, 2017).

There are two main downsides to pushing the support dates for PHP 5.6:

- Obviously, it will require the developers of PHP (us) to maintain it for a
  longer period of time, investing more time and effort than we would
  otherwise have to.
- Extending the end of support dates may reduce the sense of urgency of
  people to upgrade, and may cause people who would have otherwise upgraded
  sooner to upgrade later.

That said, many believe that sticking with the current timeline (option #3) is
simply too aggressive, and we should at least go for option #2 as it gives
people at least the same amount of time they had to upgrade from 5.5 to 5.6,
to upgrade from 5.6 to 7.0.

Further, given the 5.6 -> 7.0 upgrade is more difficult and time consuming -
the recommendation of this RFC is to go with option #1. The importance of
giving users a bit more time to upgrade was also alluded to in the PHP 5.7
RFC, although it was rejected - mainly due to concerns about defocusing the
efforts of releasing PHP 7.0 - concerns which are no longer relevant now that
7.0 has been successfully released.

Decision
````````

- Extend the support timeline of PHP 5? — **Yes**
- Extend the support timeline to: 1 year Active Support, 2 years Security Support

Name of Next Release of PHP
~~~~~~~~~~~~~~~~~~~~~~~~~~~

**From:** https://wiki.php.net/rfc/php6

Introduction
````````````

There has been some debate over what the name of the next major release of
PHP, to succeed the PHP 5.x series, should be called. This RFC is an attempt
to settle the matter once and for all.

This RFC proposes that the next major version of PHP shall be named either PHP
6 or PHP 7, based on the outcome of this vote. In the following arguments for
both sides are presented.

Historical context
``````````````````

The reason why this question even comes up, is that there has been a previous
attempt at a new major version, which was started in 2005 and abandoned in
2010 due to difficulties in the Unicode implementation. Apart from
language-integrated Unicode support, most features added for that version were
integrated either in PHP 5.3 or PHP 5.4.

This previous attempt at a new major version was also developed under the name
of PHP 6 and as such there are various resources referring to it, including a
number of books. There is concern that there might be confusion between the
abandoned previous attempt and the work that is currently happening.

The Case for PHP 7
``````````````````

The case for choosing 7 as the next major version for PHP is comprised from 2
key elements - there are no good reasons not to do it, and several good
reasons to do it.

No good reasons NOT to skip version 6
#####################################

Regarding the first element, it seems that many people are concerned that if
we skip a version, we somehow cause confusion or break away from our
versioning scheme.

The main confusion point cited by proponents of 'PHP 6' was that people will
wonder 'how come we suddenly have PHP 7 and without having PHP 6?' - however,
this is really much more of a trivia question than a cause for confusion. For
obvious reasons, it will be clear that 7 is the latest version and even if
there is 6 out there, 7 is newer and better.

We also wouldn't be breaking away or even changing our current versioning
scheme. We're only skipping a version, while keeping everything about our
versioning scheme intact.

Strong reasons of why we actually should skip version 6 into 7
##############################################################

There are several reasons of why we shouldn't reuse version 6 for the next
major version of PHP.

- First and foremost, PHP 6 already existed and it was something completely
  different. The decimal system (or more accurately the infinite supply of
  numbers we have) makes it easy for us to skip a version, with plenty more
  left for future versions to come.
- While it's true that the other PHP 6 never reached General Availability, it
  was still a very widely published and well-known project conducted by
  php.net that will share absolutely nothing with the version that is under
  discussion now. Anybody who knew what PHP 6 is (and there are many) will
  have a strong misconception in his or her mind as to the contents and
  features of this new upcoming version (essentially, that it's all about
  Unicode).
- PHP 6, the original PHP 6, has been discussed in detail in many PHP
  conferences. It was taught to users as a done-deal, including detailed
  explanations about features and behavior (by php.net developers, not 'evil'
  book authors).
- PHP 6 was widely known not only within the Internals community, but around
  the PHP community at large. It was a high profile project that many - if
  not most - PHP community members knew about.
- There's lots of PHP 6 information, about the original PHP 6, that exists
  around the web. Books are the smallest part of the problem.
- Unlike the 'trivia question' of 'why did we skip into 7?', reusing version
  6 is likely to call real confusion in people's minds, with ample
  information on two completely different versions with entirely different
  feature sets that have the exact same name.
- Skipping versions isn't unprecedented or uncommon in both open source
  projects and commercial products. MariaDB, jumped all the way up to version
  10.0 to avoid confusion, Netscape Communicator skipped version 5.0 directly
  into 6.0, and Symantec skipped version 13. Each and every one of those had
  different reasons for the skipping, but the common denominator is that
  skipping versions is hardly a big deal.
- Version 6 is generally associated with failure in the world of dynamic
  languages. PHP 6 was a failure; Perl 6 was a failure. It's actually
  associated with failure also outside the dynamic language world - MySQL 6
  also existed but never released. The perception of version 6 as a failure -
  not as a superstition but as a real world fact (similar to the association
  of the word 'Vista' with failure) - will reflect badly on this PHP version.
- The case for 6 is mostly a rebuttal of some of the points above, but
  without providing a strong case for why we *shouldn't* skip version 6. If
  we go with PHP 7, the worst case scenario is that we needlessly skipped a
  version. We'd still have an infinite supply of major versions at our
  disposal for future use. If, however, we pick 6 instead of 7 - the worst
  case scenario is widespread confusion in our community and potential
  negative perception about this version.

As a special non serious bonus, 7 is perceived as a lucky number in both the
Western world and Chinese culture. A little bit of luck never hurt anybody.
http://en.wikipedia.org/wiki/Numbers_in_Chinese_culture (no, we're not truly
seeing it as a real advantage - the case for 7 is very strong without it).

Summary
#######

Version 6 is already taken by a highly publicized project that is in the minds
of a very large chunk of PHP developers, internals and general PHP community
alike.

We risk nothing by calling it PHP 7. We risk confusion and negative perception
if we insist on reusing 6 for a completely different project.

Taking a risk that stands to yield absolutely no reward is not a good
strategy.

The Case for PHP 6
``````````````````

- According to our current release process and semantic versioning, the next
  major version after PHP 5 should be PHP 6. Unless there are very strong
  reasons to the contrary, we should not abandon our current version
  numbering scheme.
- While there exists a number of resources about the previous attempt at a
  PHP 6 release, these will be quickly displaced once PHP 6 is actually
  released. This applies both to blog posts, which will be (and partially
  already are) displaced by newer content, and books, which will receive
  negative reviews because they do not actually cover the version of PHP they
  claim to cover.
- By now there are also many resources which refer to the next major version
  as “PHP 6”, without having any relation to the abandoned previous attempt.
  This includes anything from blog posts and discussions about features for
  the upcoming version, to RFCs and design documents in this wiki. Calling
  the next major version “PHP 7” instead will cause confusion in this
  direction.
- In OTR discussions about a new major version, it is nearly always referred
  to as “PHP 6”. Given that the current version is PHP 5, people
  understandably jump to the conclusion that the next one will be “PHP 6” and
  refer to it as such. In the minds of many devs “PHP 6” is already deeply
  ingrained as the name of the next major.
- While many participants on the internals mailing list were involved in the
  original PHP 6 effort and as such are acutely aware of its existence, the
  larger PHP community is not. While discussing this RFC with various
  developers, many did not really understand why this was even a question,
  because they were no more than vaguely aware that there was something like
  PHP 6 in the past. As such wrong expectations due to confusion about the
  version number should be minimal.
- While there has certainly been precedent for missing version numbers, this
  usually occurs in the context of larger changes to the versioning scheme.
  For example, when Java went from 1.4 to 5.0, it's clear that the numbering
  system changed. The existing precedent suggests going to PHP 2016 or
  something equally distinct, rather than just skipping a version. (No, this
  is not a serious suggestion.)

Vote
````

A 50%+1 (simple majority) vote with two options, “PHP 6” and “PHP 7”, is
proposed. If more votes are for PHP 6, that shall be the name of the next
major release of PHP. Otherwise, if more of votes are for PHP 7, that shall be
its name.

Decision
````````

- PHP 6: 24
- PHP 7: **58**


PHP 7.0 Timeline
~~~~~~~~~~~~~~~~

**From:** https://wiki.php.net/rfc/php7timeline

Introduction
````````````

With key decisions about both the version number and the engine for PHP 7
behind us, it's time to define an agreed-upon timeline so that all
contributors can align around it. The purpose of this RFC is to define a one
year timeline for the delivery of PHP 7.0, with a projected release date of
November 2015.

Proposal
````````

As the competitive landscape for PHP is evolving, the proposal is to shorten
that timeline as much as possible while still taking advantage of the unique
opportunities available to us due to the major version number change. A one
year timeline will allow us a fair amount of time to work on changes that are
only allowed in major versions - namely, ones that break compatibility.
Arguably, while we should definitely take the opportunity to implement
compatibility-breaking changes in 7.0, we also shouldn't turn it into a
compatibility-breaking festival, as the more we break, the more likely it is
users would delay upgrades, stay with old, insecure versions - or even
consider other alternative options. RFCs that don't explicitly require a major
version change (i.e., ones that don't break compatibility) - can also be
proposed, but they should be secondary, as they can equally make it into
future minor versions (7.1, 7.2, etc.).

Proposed Milestones
###################

=====================================================  ==================================== =======
Milestone                                              Timeline                             Comment
=====================================================  ==================================== =======
1. Line up any remaining RFCs that target PHP 7.0.     Now - Mar 15 (4+ additional months)  We're already well under way with doing that, with the PHPNG, AST, uniform variable syntax, etc.
2. Finalize implementation & testing of new features.  Mar 16 - Jun 15 (3 months)
3. Release Candidate (RC) cycles                       Jun 16 - Oct 15 (3 months)           Subject to quality!
4. GA/Release                                          Mid October 2015                     Subject to quality!
=====================================================  ==================================== =======

It's worth noting that the 3rd and 4th milestones will be quality dependent.
If we have evidence that suggests that PHP 7 isn't sufficiently mature to go
into the RC stage in June, or GA in October - we should of course adjust the
timeline accordingly, and not push out a half-baked release. However, the goal
would be to stick as much as possible to the deadline of new going-into-7.0
RFCs, and strive to follow the timelines for the 2nd and 3rd milestones as
much as possible, to ensure an October 2015 release of PHP 7.0.

Cleaning Up Unmaintained Extensions (PHP 7.3)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Introduction
````````````

We have a number of extensions that have no assigned maintainer. The proposal
is either to find a maintainer for them or move them out of core. The RFC
proposes the procedure for doing this for 7.3 release and repeat it for each
subsequent release.

Proposal
````````

For the extensions that have no maintainers, the proposal is to:

- Issue a call for maintainership on internals list (and maybe other venues,
  such as thematic PHP communities, as seen appropriate).
- If a maintainer candidate(s) show up:
- If they are already committers, assign them as maintainers. The extension
  is considered maintained from now on, no further action needed.
- Otherwise, ask them to submit a couple of patches for existing bugs in the
  extension, of their choice. If these are ok, issue them php.net account
  with appropriate permissions and assign them as maintainers for the claimed
  extension. If extensions has no bugs to fix, assign them as maintainers
  immediately (php.net account may not yet be needed).
- If within 3 weeks nobody steps up as a maintainer for extension, it is
  considered orphaned.
- All orphaned extensions are converted to PECL modules and removed from core
  repository. There should be a public announcement procedure before this
  happens, with the details not defined of this RFC but to be worked out by
  RMs and the community (either with separate RFC or just by consensus).
- In case there are objections to moving unmaintained extension to PECL,
  separate RFC vote can be held about the move, initiated by the RMs of the
  current release or any interested party. The decision can be taken for each
  extension individually.

Option: for some extensions, which are clearly needed but nobody stepped up in
person to claim maintainership, we can have designated “community maintained”
status, which would mean PHP developers as a group have shared responsibility
for this extension. This is to be accepted as an inferior solution, which need
to be eventually resolved by either finding a maintainer or finding an
alternative for the extension.

To be clear, the ideal result of this process is that all core extensions find
a maintainer. So we want to have the process biased towards finding one, not
removing extensions from core. However, if we fail to do so, we rather claim
it explicitly than ship buggy, unmaintained and possibly insecure code to the
users.

Candidate extensions
````````````````````

These are core extensions for which there is no official maintainer
registered. Please note that the exact content of this list is not part of the
vote - it can change with new maintainers coming up or old maintainers
retiring, and there probably would be a separate list maintained as necessary.

============  =======================  ===============  ==========  ==================
Extension     Bugs in DB (minus reqs)  Oldest open bug  Newest bug  Most recent bugfix
============  =======================  ===============  ==========  ==================
enchant       4                        2008-02-21       2009-10-28  2008-02-23
ftp           26                       2010-05-10       2016-06-06  2016-08-16
gettext       6                        2007-12-11       2015-09-24  2015-08-31
pdo_odbc      26                       2007-06-22       2016-01-18  2009-12-11
readline      4                        2012-03-31       2001-01-26  2015-12-11
pspell        2                        2014-03-19       2016-04-19  2008-09-16
sysvmsg       No bug category
sysvsem       19                       2002-04-29       2016-04-04  2014-09-10
sysvshm       No bug category
wddx          6                        2006-03-17       2016-08-11  2016-08-11
============  =======================  ===============  ==========  ==================

Backward Incompatible Changes
`````````````````````````````

Default build of PHP would not have the extensions that will be moved out.
They still could be built from PECL sources. The focus of this RFC, however,
is for establishing procedures for unmaintained extensions rather than dealing
with specific extensions, so decision about each extension can be taken
separately.

Proposed PHP Version(s)
```````````````````````

The process is proposed for 7.3 and all future PHP versions.

Future Scope
````````````

We may need to refresh the list of current maintainers (since some maintainers
have moved on) and repeat the process in the future.

The proposed procedure is to add years to each maintainer's status in the
maintainers list, with the year to be updated manually by the maintainer. If
by end of January of the year the last updated year is past the last year
(e.g., 2018 or less in January 2020), the extension is deemed to be abandoned
by the maintainer. In this case, the maintainer would be asked to clarify the
maintainership status, and absent response or with a negative response, the
extension will be considered having no maintainer. This can be changed at any
moment if the existing or new maintainer comes up (again, the priority is
always towards finding the maintainer, not moving stuff out).

To initiate this procedure, the years should be initialized with the last
commit or last bug response from the maintainer to the maintained extension
code or bugs.

