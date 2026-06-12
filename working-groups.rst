################
 Working Groups
################

**************
 Introduction
**************

This document establishes a framework for the creation, operation, and
dissolution of working groups within the PHP Project. It provides a structured,
transparent mechanism for managing discrete projects or activities (whether
technical, infrastructural, or otherwise) undertaken by the Community. As such,
it ensures that each working group is clearly chartered, time-bound, and
actively led, thereby addressing organizational gaps that often leave new and
existing volunteers uncertain about who to talk to or how to contribute.

Terms
=====

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in `BCP 14
<https://www.rfc-editor.org/info/bcp14/>`_ [ `RFC2119
<https://www.rfc-editor.org/info/rfc2119/>`_ ] [ `RFC8174
<https://www.rfc-editor.org/info/rfc8174/>`_ ] when, and only when, they appear
in all capitals, as shown here.

"Community" means the broad, worldwide group of individuals and organizations
who use or have an interest in the PHP Project.

"PHP Project" means the websites, documentation, infrastructure, mailing lists,
and software accessible through PHP.net and managed as part of the whole
project.

"PHP RFC process" means the process for proposing changes to the PHP programming
language or PHP Project policies, as defined in `Feature Proposals
<https://github.com/php/policies/blob/main/feature-proposals.rst>`_.

****************
 Working Groups
****************

Creation
========

Using the PHP RFC process, any Community member or group of Community members
may propose a working group.

Scope
=====

Each working group is responsible for the active management of one or more PHP
Project projects or activities identified by the working group charter, which
may include, without limitation, the creation or maintenance of open source
software, infrastructure, outreach and educational programs, or language and
policy change proposals.

Creating a working group is not a requirement for creating a PHP RFC, but
working groups MAY propose PHP RFCs as part of their activities. If a working
group's activities include making changes to the PHP programming language and/or
PHP Project policies, the working group MUST follow the PHP RFC process to
propose these changes.

Proposal
========

The proposal to create a working group MUST follow the PHP RFC process.

The PHP RFC that proposes a working group MUST include the working group
charter, and the charter MUST specify at least the following:

#. **Name.** The name of the working group.

#. **Purpose.** The purpose and mission of the working group and how it relates
   to the PHP Project.

#. **Duration.** How long the working group is expected to last. This is a time
   frame or a condition, such as fulfillment of the working group's purpose.

#. **Activities.** The project(s) and/or activity(ies) the working group will
   undertake.

#. **Membership.** The process by which the working group will select its
   members and chairperson and any qualifications for membership. The working
   group MAY list initial members and chairperson as part of its charter, if
   applicable.

#. **Communication Plan.** How the working group plans to communicate with its
   members, the PHP Project, and the Community.

The working group charter MAY include sections not defined here.

Changes to the working group name, purpose, and duration MUST use the PHP RFC
process. Other sections of the working group charter MAY be amended from
time-to-time by members of the working group through consensus with other
members of the working group.

Responsibilities
================

Each working group SHALL designate a chairperson who is the primary responsible
party for projects and activities managed by the group. The chairperson MAY
establish rules and procedures for the day-to-day management of projects and
activities for which the group is responsible.

Each working group MUST publish an annual public report describing its
activities and accomplishments. In addition, each group SHOULD publish quarterly
or semiannual public updates to inform the Community on the status of its
activities.

Working group operations, including but not limited to meetings, discussions,
decisions, and work activity, SHOULD be open and transparent. Exceptions include
situations in which privacy or sensitive information must be protected.

Working Group Policies
======================

Through the PHP RFC process, the Community may set policies or procedures which
apply to working groups. These policies or procedures MAY apply to individual
working groups, multiple working groups, or all working groups. The chairpersons
of affected working groups are responsible for implementing and adhering to the
policies or procedures which apply to them.

Duration and Dissolution
========================

The working group charter MUST specify the group's duration. When the duration
as stated in the charter is reached, the working group is automatically
dissolved.

Some working groups do not have an obvious duration (e.g., infrastructure). In
these cases, the working group charter MAY specify a duration of "indefinite."

The Community may propose a dissolution RFC to dissolve a working group at any
time. The RFC to dissolve a working group MUST include a statement explaining
the reason(s) for dissolving the working group.

When a working group nears dissolution or is dissolved, either at the time
stated in the working group charter or by the acceptance vote of a dissolution
RFC, the working group MAY be rechartered by creating a new PHP RFC with a new
working group charter.

Charter Artifacts
=================

Upon acceptance of a working group charter RFC, the working group charter MUST
be added to the ``working-groups/`` subdirectory of the `PHP Policies repository
<https://github.com/php/policies>`_. Upon dissolution of a working group, the
working group charter MUST be moved to the ``archive/working-groups/``
subdirectory.
