##################################################
 Social Media and Marketing Communications Policy
##################################################

.. NOTE::

   This policy was adopted by the `Social Media and Marketing Communications
   Policy RFC`_.

This policy governs the PHP project's official presence on social media and
other marketing communication platforms. It defines the platforms in scope, the
principles guiding official communications, and a division of responsibilities
between the *PHP Infrastructure Team* (which holds credentials and operates the
accounts) and the *PHP Social Media Team* (which decides what is posted).

*********
 Purpose
*********

To ensure that the PHP project communicates with its community and the broader
technology ecosystem in a consistent, accountable, and sustainable manner. The
policy separates account custody (a technical responsibility, retained by the
Infrastructure Team) from content authority (a communications responsibility,
held by an open-volunteer Social Media Team).

*******
 Scope
*******

This policy applies to all accounts officially representing the PHP project on
text-based communication platforms. At the time of adoption, these include:

-  Twitter/X (`@official_php <https://twitter.com/official_php>`_)
-  Mastodon (`@php@fosstodon.org <https://fosstodon.org/@php>`_)
-  LinkedIn (`@phpnet <https://www.linkedin.com/company/phpnet/>`_)

Changes to this list — adding a new official account or retiring an existing one
— are made by pull request to this document, following the procedures defined in
the Social Media Team's `operational policies`_.

Video platforms (for example, YouTube, TikTok, Instagram) require significant
content-production resources and are explicitly out of scope. They MAY be
addressed by a future policy update.

This policy does not govern personal accounts of community members or core
developers. Personal advocacy for PHP is encouraged and remains outside the
scope of this document.

************
 Principles
************

Official PHP communications SHALL be governed by the following principles:

#. **Reach.** PHP SHOULD maintain a presence on text-based platforms with a
   significant developer audience, subject to the discretion principle below.

#. **Discretion.** Presence on any given platform is at the project's
   discretion. Nothing in this policy obliges the project to establish or
   maintain a presence on any particular platform. A decision to add or retire
   an account MUST be deliberate and documented: it MUST follow the procedures
   defined in the Social Media Team's `operational policies`_, and a retirement
   MUST be announced on the internals mailing list before taking effect. The
   community MAY escalate a contested decision to an RFC.

#. **No silent abandonment.** While a platform is listed in the Scope_ section,
   posting SHALL continue — at minimum, automated content where the platform
   technically permits it. Ceasing activity on a listed platform other than
   through the retirement procedure violates this policy.

#. **Automation.** Communications SHOULD be automated where feasible, to
   minimize volunteer burden and ensure consistency.

#. **Neutrality.** Communications MUST focus on PHP — the language, its
   releases, security advisories, and community events — and MUST NOT take
   positions on platform politics or non-PHP commercial matters. Official
   accounts MUST NOT be used as a venue for advocacy unrelated to PHP.

#. **Shared stewardship.** Credentials for each official account MUST be held by
   multiple Infrastructure Team members, with documented succession.

#. **Transparency.** This policy SHALL be publicly available and versioned via
   the RFC process. The current Social Media Team roster SHALL be public.

****************************
 Roles and Responsibilities
****************************

PHP Infrastructure Team: Account Custody
========================================

For the purposes of this policy, the *PHP Infrastructure Team* is the existing
group of volunteers who maintain the PHP project's infrastructure, coordinated
through the ``systems@php.net`` mailing list and the `php/infrastructure`_
repository.

The PHP Infrastructure Team is responsible for the technical custody and
operation of official accounts. The Infrastructure Team:

-  MUST hold the credentials for all official PHP social media accounts.

-  MUST maintain secure credential storage accessible to a minimum of three (3)
   authorized holders per account.

-  MUST implement and maintain automation for cross-platform posting where the
   platform supports it.

-  MUST ensure credential succession when a holder steps down.

-  MUST maintain a public list of the credential holders for each official
   account (for example, in the `php/infrastructure`_ repository or in this
   repository).

-  SHALL handle technical operations such as account recovery, security
   incidents, and platform compliance.

-  SHALL act on posting requests from the Social Media Team for content that is
   not posted automatically, and SHOULD provide the Social Media Team with the
   technical means (for example, scoped access, automation hooks, or a posting
   workflow) to publish approved content efficiently.

The Infrastructure Team's role is operational and technical. It does not decide
content.

PHP Social Media Team: Content Authority
========================================

The *PHP Social Media Team* is responsible for content on official PHP accounts.
The Social Media Team:

-  SHALL decide what is posted on official channels, including messaging,
   timing, and tone, subject to the `Prohibited Content`_ rules below.
-  SHALL develop and maintain its own `operational policies`_ (see below).
-  SHOULD coordinate with the Infrastructure Team on technical execution.
-  SHOULD advise on platform presence, audience strategy, and communications
   priorities.
-  MAY initiate marketing efforts beyond automated content, as defined in its
   operational policies.
-  MAY delegate specific responsibilities to the PHP Foundation (see `Delegation
   to the PHP Foundation`_).

Operational Policies
--------------------

The Social Media Team SHALL develop and maintain its own operational policies —
for example, content categories and approval workflow, procedures for adding and
retiring official accounts, and member onboarding. These operational policies:

-  SHALL be maintained in the `Social Media Team Operations`_ document in this
   repository.
-  SHALL be developed and amended through an open and transparent process, by
   pull request to this repository. Changes do NOT require an RFC.
-  MUST NOT conflict with this policy. In case of conflict, this policy
   prevails.

Composition
-----------

The Social Media Team is composed of open volunteers from the PHP project
community. Membership is self-organized: the team SHOULD agree on its own
internal processes for adding and removing members, coordinating posts, and
resolving disagreements.

-  Anyone interested in joining MAY propose themselves to the existing team. The
   team SHOULD respond within a reasonable time.

-  Each member SHOULD have a demonstrated connection to the PHP community (for
   example, contributions to php-src, the documentation, the infrastructure, a
   PHP user group, or comparable involvement).

-  The current roster is maintained in the `Current Members`_ section below and
   SHOULD be updated by pull request to this repository when membership changes.

-  Additions to the roster SHALL be announced on the internals mailing list, and
   the roster pull request SHOULD remain open for at least one (1) week to allow
   community comment. Sustained objections SHOULD be resolved before the pull
   request is merged.

-  The team SHOULD have at least three (3) active members at all times. If the
   team drops below this number, the remaining members SHOULD recruit
   replacements within thirty (30) days; if they cannot, the matter SHOULD be
   raised on the internals mailing list.

-  While membership is below three, automated posting SHALL continue; content
   requiring the team's approval (as defined in its operational policies) is
   paused.

The team MAY remove a member according to its internal process. In addition, the
team is accountable to the project as a whole: the community MAY remove a
member, or reconstitute the team, through the project's RFC process.

Members of the Social Media Team do not, by virtue of that membership, hold
account credentials. Credential custody remains with the Infrastructure Team. An
individual MAY belong to both teams if they meet the criteria for each.

Delegation to the PHP Foundation
--------------------------------

The Social Media Team MAY delegate specific responsibilities to the `PHP
Foundation`_ — for example, drafting marketing initiatives, curating content, or
running coordinated campaigns. Such delegation:

-  MAY be open-ended or scoped to particular content categories.
-  SHALL be recorded in this policy file or in a sub-document under this
   repository, linked from this section.
-  MAY be revoked by the team at any time.

Delegation does not transfer credential custody — credentials remain with the
Infrastructure Team. The Social Media Team retains overall content authority and
remains accountable for content posted under delegated authority.

********************
 Prohibited Content
********************

Content categories, approval workflows, and other content processes are defined
by the Social Media Team in its `operational policies`_. Regardless of those
policies, official PHP accounts MUST NOT post:

-  Political statements unrelated to PHP
-  Commercial endorsements of products or services unrelated to PHP
-  Personal opinions presented as the PHP project's official position
-  Personal grievances or interpersonal disputes between contributors

Applying these rules — including judging whether a topic is related to PHP —
requires contextual judgment. That judgment rests with the Social Media Team.
Disagreements SHOULD be raised on the internals mailing list.

***********************
 Credential Management
***********************

For each official account:

-  Credentials MUST be stored securely with documented access procedures.
-  When a credential holder steps down, replacement MUST be coordinated within
   thirty (30) days.
-  Emergency access procedures MUST be documented and tested.
-  Credentials MUST NOT be shared with Social Media Team members who are not
   also part of the Infrastructure Team.

********************
 Account Transition
********************

Upon adoption of this policy:

#. The Infrastructure Team SHALL inventory all accounts currently representing
   PHP officially across platforms.

#. Current credential holders SHALL be requested to transfer credentials to the
   Infrastructure Team's secure storage within sixty (60) days.

#. If a credential holder declines or does not respond within sixty (60) days,
   the Infrastructure Team and the Social Media Team SHALL jointly determine
   whether to:

   #. Petition the platform for account recovery (where supported);
   #. Establish a new official account on that platform; or
   #. Mark the original account as non-official on PHP.net.

****************
 Implementation
****************

Automated posting SHOULD be implemented via GitHub Actions or equivalent
automation, following the model already in use for the Mastodon account.
Automations SHOULD be hosted under the PHP organization on GitHub and SHOULD be
maintainable by the Infrastructure Team. Where feasible, the Infrastructure Team
SHOULD provide the Social Media Team with self-serve mechanisms (for example, a
posting workflow or PR-based trigger) so that team-approved content does not
require manual intervention for every post.

************
 Amendments
************

This policy MAY be amended by a future RFC with a 2/3 majority approval.

The following changes do NOT require an RFC and SHOULD be made by pull request
to this repository:

-  Updates to the `Current Members`_ list.
-  Updates to the account list in the Scope_ section, following the Social Media
   Team's `operational policies`_, unless escalated by the community.
-  Changes to the `Social Media Team Operations`_ document.

*****************
 Current Members
*****************

The current roster of the PHP Social Media Team is listed below. Update by pull
request when membership changes.

-  *(To be populated upon adoption.)*

.. _operational policies: social-media/team-operations.rst

.. _php foundation: https://thephp.foundation/

.. _php/infrastructure: https://github.com/php/infrastructure

.. _social media and marketing communications policy rfc: https://wiki.php.net/rfc/social-media-policy

.. _social media team operations: social-media/team-operations.rst
