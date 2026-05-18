###################################################
 Social Media and Marketing Communications Policy
###################################################

.. NOTE::

   This policy was adopted by the `Social Media and Marketing Communications
   Policy RFC`_.

This policy governs the PHP project's official presence on social media and
other marketing communication platforms. It defines the platforms in scope,
the principles guiding official communications, and a division of
responsibilities between the *PHP Infrastructure Team* (which holds
credentials and operates the accounts) and the *PHP Social Media Team*
(which decides what is posted).

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

Changes to this list are governed by the Adding and Removing Official Accounts_ 
section.

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

#. **Reach.** PHP SHOULD maintain a presence on any text-based platform with a
   significant developer audience.
#. **Automation.** Communications SHOULD be automated where feasible, to
   minimize volunteer burden and ensure consistency.
#. **Neutrality.** Communications MUST focus on PHP — the language, its
   releases, security advisories, and community events — and MUST NOT take
   positions on platform politics or non-PHP commercial matters.
#. **Shared stewardship.** Credentials for each official account MUST be held
   by multiple Infrastructure Team members, with documented succession.
#. **Transparency.** This policy SHALL be publicly available and versioned via
   the RFC process. The current Social Media Team roster SHALL be public.

******************************
 Roles and Responsibilities
******************************

PHP Infrastructure Team: Account Custody
========================================

The PHP Infrastructure Team is responsible for the technical custody and
operation of official accounts. The Infrastructure Team:

-  MUST hold the credentials for all official PHP social media accounts.
-  MUST maintain secure credential storage accessible to a minimum of three
   (3) authorized holders per account.
-  MUST implement and maintain automation for cross-platform posting where
   the platform supports it.
-  MUST ensure credential succession when a holder steps down.
-  SHALL handle technical operations such as account recovery, security
   incidents, and platform compliance.
-  SHALL act on posting requests from the Social Media Team for non-automated
   content, and SHOULD provide the Social Media Team with the technical means
   (for example, scoped access, automation hooks, or a posting workflow) to
   publish approved content efficiently.

The Infrastructure Team's role is operational and technical. It does not
decide content.

PHP Social Media Team: Content Authority
========================================

The *PHP Social Media Team* is responsible for content on official PHP
accounts. The Social Media Team:

-  SHALL decide what is posted on official channels, including messaging,
   timing, and tone, subject to the content rules below.
-  SHOULD coordinate with the Infrastructure Team on technical execution.
-  SHOULD advise on platform presence, audience strategy, and communications
   priorities.
-  MAY initiate marketing efforts beyond automated content (see `Marketing
   Initiatives`_).
-  MAY delegate specific responsibilities to the PHP Foundation (see
   `Delegation to the PHP Foundation`_).

Composition
-----------

The Social Media Team is composed of open volunteers from the PHP project
community. Membership is self-organized: the team SHOULD agree on its own
internal processes for adding and removing members, coordinating posts, and
resolving disagreements.

-  Anyone interested in joining MAY propose themselves to the existing team.
   The team SHOULD respond within a reasonable time.
-  Each member SHOULD have a demonstrated connection to the PHP community
   (for example, contributions to php-src, the documentation, the
   infrastructure, a PHP user group, or comparable involvement).
-  The current roster is maintained in the `Current Members`_ section below
   and SHOULD be updated by pull request to this repository when membership
   changes.
-  The team SHOULD have at least three (3) active members at all times. If
   the team drops below this number, the remaining members SHOULD recruit
   replacements within thirty (30) days; if they cannot, the matter SHOULD
   be raised on the internals mailing list.
-  While membership is below three, automated content SHALL continue; 
   curated content and marketing initiatives are paused.

Members of the Social Media Team do not, by virtue of that membership, hold
account credentials. Credential custody remains with the Infrastructure Team.
An individual MAY belong to both teams if they meet the criteria for each.

Delegation to the PHP Foundation
--------------------------------

The Social Media Team MAY delegate specific responsibilities to the `PHP
Foundation`_ — for example, drafting marketing initiatives, curating content,
or running coordinated campaigns. Such delegation:

-  MAY be open-ended or scoped to particular content categories.
-  SHALL be recorded in this policy file or in a sub-document under this 
   repository, linked from this section.
-  MAY be revoked by the team at any time.

Delegation does not transfer credential custody — credentials remain with the
Infrastructure Team. The Social Media Team retains overall content authority
and remains accountable for content posted under delegated authority.

********************
 Content Categories
********************

Automated Content
=================

The following content types are suitable for automated cross-platform posting
and DO NOT require per-post approval:

-  Release announcements (major, minor, and patch versions)
-  Security advisories and CVE announcements
-  RFC voting results
-  Conference and event announcements published through official PHP channels
-  Other news and announcements published on the `PHP.net news feed
   <https://www.php.net/archive/>`_

Automated content is triggered by project events such as releases, security
commits, vote closures, or new entries in the PHP.net news feed.

Curated Content
===============

The following content types require approval from the Social Media Team
before posting:

-  Milestone announcements
-  Anniversary and celebration posts
-  Blog post promotions
-  Any other non-automated content

The Social Media Team MAY define lightweight internal procedures for
approving curated content (for example, a minimum number of team members
signing off). The Infrastructure Team SHALL post approved curated content.

Marketing Initiatives
=====================

Proactive marketing efforts beyond the above categories MAY be undertaken
by the Social Media Team. These MAY include:

-  Coordinated campaigns
-  Responses to industry narratives
-  Developer outreach initiatives
-  Cross-promotion with ecosystem projects

The Social Media Team MAY delegate marketing initiatives to the PHP
Foundation, as described in `Delegation to the PHP Foundation`_.

Prohibited Content
==================

Official PHP accounts MUST NOT post:

-  Political statements unrelated to PHP
-  Commercial endorsements of products or services unrelated to PHP
-  Personal opinions presented as the PHP project's official position
-  Personal grievances or interpersonal disputes between contributors

***********************
 Credential Management
***********************

For each official account:

-  Credentials MUST be stored securely with documented access procedures.
-  When a credential holder steps down, replacement MUST be coordinated
   within thirty (30) days.
-  Emergency access procedures MUST be documented and tested.
-  Credentials MUST NOT be shared with Social Media Team members who are not
   also part of the Infrastructure Team.

********************
 Account Transition
********************

Upon adoption of this policy:

#. The Infrastructure Team SHALL inventory all accounts currently representing
   PHP officially across platforms.
#. Current credential holders SHALL be requested to transfer credentials to
   the Infrastructure Team's secure storage within sixty (60) days.
#. If a credential holder declines or does not respond within sixty (60) days,
   the Infrastructure Team and the Social Media Team SHALL jointly determine
   whether to:

   #. Petition the platform for account recovery (where supported);
   #. Establish a new official account on that platform; or
   #. Mark the original account as non-official on PHP.net.

***************************************
 Adding and Removing Official Accounts
***************************************

The official list of accounts is defined in the `Scope`_ section above.
Changes to the list — adding a new official account or retiring an existing
one — are made by pull request to this document.

Adding an Account
=================

#. The Social Media Team agrees, per its internal process, that a new
   account on a given platform should be created.
#. The Social Media Team requests the Infrastructure Team to create the
   account and configure credentials per the `Credential Management`_
   section.
#. The Infrastructure Team confirms creation.
#. The `Scope`_ list is updated by pull request. The account becomes
   official once the pull request is merged.

Retiring or Removing an Account
===============================

The Social Media Team MAY decide to retire an official account. Available
options include:

-  **Pause posting.** Keep the account, stop posting, and optionally pin a
   notice referring readers to other channels.
-  **Mark non-official.** Retain the account but remove it from PHP.net
   and from the `Scope`_ list.
-  **Archive or delete.** Close or delete the account through the platform,
   where supported by the platform's policies.

The chosen action SHALL be executed by the Infrastructure Team. Where the
account is linked from PHP.net, the link SHOULD be updated or removed as
part of the same change. The `Scope`_ list MUST be updated by pull request.

Where an account has established public reach (for example, a sizable
follower count (≥1k followers) or a long-standing presence (≥2 years presence)), 
the Social Media Team SHOULD announce the proposed retirement on the internals 
mailing list before acting, to give the community an opportunity to comment. 
The community MAY request an RFC if it considers the retirement a project-level 
decision.

Recognizing an Existing Third-Party-Controlled Account
======================================================

An existing community-run account MAY be recognized as official by
following the `Account Transition`_ procedure: credential transfer to the
Infrastructure Team, addition to the `Scope`_ list via pull request, and
adoption of this policy's content rules.

****************
 Implementation
****************

Automated posting SHOULD be implemented via GitHub Actions or equivalent
automation, following the model already in use for the Mastodon account.
Automations SHOULD be hosted under the PHP organization on GitHub and
SHOULD be maintainable by the Infrastructure Team. Where feasible, the
Infrastructure Team SHOULD provide the Social Media Team with self-serve
mechanisms (for example, a posting workflow or PR-based trigger) so that
curated content does not require manual intervention for every post.

************
 Amendments
************

This policy MAY be amended by a future RFC with a 2/3 majority approval.
Updates to the `Current Members`_ list do not require an RFC and SHOULD be
made by pull request.

Routine additions and retirements per Adding and Removing Official Accounts_ do not
  require an RFC unless escalated by the community.

*****************
 Current Members
*****************

The current roster of the PHP Social Media Team is listed below. Update by
pull request when membership changes.

-  *(To be populated upon adoption.)*

.. _php foundation: https://thephp.foundation/

.. _social media and marketing communications policy rfc: https://wiki.php.net/rfc/social-media-policy
