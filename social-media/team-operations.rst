##############################
 Social Media Team Operations
##############################

.. NOTE::

   This document contains the operational policies of the *PHP Social Media
   Team*, as provided for by the `Social Media and Marketing Communications
   Policy`_. It is maintained by the Social Media Team and amended by pull
   request to this repository — changes do not require an RFC. It must not
   conflict with the policy; in case of conflict, the policy prevails.

This document defines how the Social Media Team operates in practice: which
content is posted automatically, which content requires the team's approval, and
how official accounts are added and retired. The list of official accounts, the
`Prohibited Content`_ rules, and the division of responsibilities between the
Social Media Team and the Infrastructure Team are defined in the `Social Media
and Marketing Communications Policy`_.

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

The following content types require approval from the Social Media Team before
posting:

-  Milestone announcements
-  Anniversary and celebration posts
-  Blog post promotions
-  Any other non-automated content

The Social Media Team MAY define lightweight internal procedures for approving
curated content (for example, a minimum number of team members signing off). The
Infrastructure Team SHALL post approved curated content.

Marketing Initiatives
=====================

Proactive marketing efforts beyond the above categories MAY be undertaken by the
Social Media Team. These MAY include:

-  Coordinated campaigns
-  Responses to industry narratives
-  Developer outreach initiatives
-  Cross-promotion with ecosystem projects

The Social Media Team MAY delegate marketing initiatives to the PHP Foundation,
as described in the policy's `Delegation to the PHP Foundation`_ section.

***************************************
 Adding and Removing Official Accounts
***************************************

The official list of accounts is defined in the policy's Scope_ section. Changes
to the list — adding a new official account or retiring an existing one — are
made by pull request to the policy document.

Adding an Account
=================

#. The Social Media Team agrees, per its internal process, that a new account on
   a given platform should be created.

#. The Social Media Team assesses the platform — its developer audience and its
   overall fit for an official PHP presence — per the policy's reach and
   `discretion principles`_.

#. The Social Media Team requests the Infrastructure Team to create the account
   and configure credentials per the policy's `Credential Management`_ section.

#. The Infrastructure Team confirms creation.

#. The Scope_ list is updated by pull request. The account becomes official once
   the pull request is merged.

Retiring or Removing an Account
===============================

The Social Media Team MAY decide to retire an official account. Available
options include:

-  **Pause posting.** Keep the account, stop posting, and pin a notice referring
   readers to other channels.
-  **Mark non-official.** Retain the account but remove it from PHP.net and from
   the Scope_ list.
-  **Archive or delete.** Close or delete the account through the platform,
   where supported by the platform's policies.

The chosen action SHALL be executed by the Infrastructure Team. Where the
account is linked from PHP.net, the link SHOULD be updated or removed as part of
the same change. The Scope_ list MUST be updated by pull request.

Where an account has established public reach (for example, a sizable follower
count (≥1k followers) or a long-standing presence (≥2 years presence)), the
Social Media Team SHOULD announce the proposed retirement on the internals
mailing list before acting, to give the community an opportunity to comment. The
community MAY request an RFC if it considers the retirement a project-level
decision.

Recognizing an Existing Third-Party-Controlled Account
======================================================

An existing community-run account MAY be recognized as official by following the
policy's `Account Transition`_ procedure: credential transfer to the
Infrastructure Team, addition to the Scope_ list via pull request, and adoption
of the policy's content rules.

.. _account transition: ../social-media-and-marketing-communications.rst#account-transition

.. _credential management: ../social-media-and-marketing-communications.rst#credential-management

.. _delegation to the php foundation: ../social-media-and-marketing-communications.rst#delegation-to-the-php-foundation

.. _discretion principles: ../social-media-and-marketing-communications.rst#principles

.. _prohibited content: ../social-media-and-marketing-communications.rst#prohibited-content

.. _scope: ../social-media-and-marketing-communications.rst#scope

.. _social media and marketing communications policy: ../social-media-and-marketing-communications.rst
