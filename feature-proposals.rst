###################
 Feature Proposals
###################

**************
 Introduction
**************

This document describes the procedure to propose an idea for adoption by the PHP
community and decide if the community accepts or rejects the idea.

The change process involves three phases: Initiation, Discussion, and Voting.

*********************
 Proposal Initiation
*********************

A proposal is formally initiated by creating an RFC on the PHP Wiki and
announcing it on the ``internals@lists.php.net`` mailing list.

The official RFC discussion thread MUST use the prefix ``[RFC]`` followed by the
title of the RFC as the Subject. The email MUST include a link to the Wiki page
containing the RFC. The link to the mailing list archives of the discussion
thread MUST be added to the RFC as soon as possible and no later than the
announcement of the start of the vote.

The discussion thread MUST be initiated by one of the RFC's authors. If the
proposal is a repeated one, re-proposed by somebody else, the proposer MUST
discuss it with the original author and add themselves to the RFC author list
before proposing it. If the original RFC authors do not agree or do not respond,
a new Wiki page containing an RFC with a unique title MUST be created. In this
case the original RFC's title is commonly suffixed with ``v2`` to indicate the
relationship with the original RFC.

A proposal or proposal concept MAY be discussed informally on the list prior
to an official initiation post.  In many cases that is encouraged to get a
sense of how well received a proposal would be.  However, that does not count
toward the Discussion Phase.

******************
 Discussion Phase
******************

In the Discussion Phase, the community may review, discuss, and offer suggestions
for improving the RFC, as extensive or minimalist as they see fit.  However,
unrelated discussions that spin off to discuss other, related topics SHOULD
be moved to their own email threads to minimize noise.

=================
Types of changes
=================

The author(s) of the RFC MAY make changes to the proposal at any time during the
discussion.  Changes broadly fall into one of three categories:

- **Major changes** to the RFC text include any changes that would lead to a change in
  the implementation, particularly any changes to the proposed semantics or
  syntax, updating the API stub. It also includes adding, changing or removing
  any voting widget.
- **Minor** changes to the RFC text include adding new examples, updating existing
  examples, adding additional explanation or clarification, or any other changes
  that are not purely editorial.
- **Editorial changes** to the RFC text include non-substantive changes, such as
  spelling, typos, changing section labels, bug fixes to existing code examples,
  small rewordings of descriptions, and so forth.

If it is unclear what level a change belongs in, the author(s) SHOULD assume the
higher one.

Major and minor changes MUST be announced in the official discussion thread,
either in a dedicated email summarizing a list of changes or in a reply to
another email that clearly indicates that changes to the RFC text have been made
in response to that email.  If a series of changes are included together, the whole
announcement belongs to the highest level of any of the involved changes.  The
initial proposal of the RFC is considered a Major change announcement.

================
Cooldown period
================

Both Major and Minor change announcements trigger a "cooldown period" to allow for
sufficient discussion of the related changes.  During the cooldown period, no vote
may be called.  Editorial changes do not trigger a cooldown period.

- The cooldown after a Major change announcement is 2 weeks (336 hours).
- The cooldown after a Minor announcement is 1 week (168 hours).

By implication, it means the minimum discussion period for any RFC is 2 weeks,
assuming no changes are made after the initial proposal.

Cooldowns overlap, so if a Major change is announced, and 3 days later a Minor
change is announced, the vote may be called 11 days (14 - 3) later.

====================
Discussion lifetime
====================

The discussion is not required to go to a vote at any particular point.  The author(s)
MAY continue the discussion as long as they wish.  The author(s) SHOULD
be mindful of holiday periods or in cases of significant activity on the mailing list
to allow everyone to catch up with the discussion.

In order to keep RFCs "fresh," their discussion threads must have a minimum level of
activity.  Any message to the discussion thread from anyone other than an Intent to Vote
is sufficient to keep the RFC active.  Once an RFC discussion goes inactive, any
new post will "reactivate" the discussion and trigger a new cooldown period.

- If it has been 6 weeks since the last message, the cooldown is 1 week (168 hours).
- If it has been 3 months since the last message, the cooldown is 2 week (336 hours).

**************
 Voting Phase
**************

=====================
Voting prerequisites
=====================

Prior to starting a vote, an RFC author MUST post an Intent to Vote message to
the discussion thread.  The post MUST be made at least two days and no more than 1 week
(168 hours) before the vote is officially opened.  Any feedback posted after the Intent
to Vote message is sent SHOULD be treated the same as if it had been sent earlier,
and any Major or Minor changes that result MUST trigger a new cooldown period,
canceling the Intent to Vote.

An RFC author MAY start a vote at any time, provided that:

- There is no cooldown period still active.
- The discussion thread is not inactive.
- The author has posted an intent to open the vote at least 48 hours prior, and no more
  than one week prior.
- There is no ongoing relevant and substantive discussion still happening in the thread.
  The author(s) may determine what qualifies as relevant and substantive, but SHOULD be
  liberal in interpreting that.

If there are any secondary votes included, the RFC text describing the vote MUST include
whether the secondary vote is plurality or Single-Transferrable Vote, how ties will be handled,
whether it is a 2/3 majority Yes/No or a 50% threshold, and any other pertinent information
to ensure the implications of the secondary vote are clearly understood.

=================
Voting procedure
=================

The actual start of the vote MUST be announced on the mailing list in a separate
thread with a ``[VOTE]`` prefix followed by the RFC title as the Subject.

The voting announcement email MUST include:

- A link to the Wiki page of the RFC.
- A link to the discussion thread.
- A notice if there are multiple votes to cast, as each requires a separate form submission.
- The exact date and time the vote will end, with minute precision and timezone.

The end of the vote MUST additionally be specified in the voting widget on the
RFC so that it will auto-close at the specified timestamp.

The link to the mailing list archives of the voting thread MUST be added to
the RFC as soon as possible and no later than the announcement of the results of the vote.

The voting period MUST be at least two weeks (336 hours), but MAY be up to
four weeks if necessary to avoid conflict with well-known holiday periods.

Due to the significance of the end-of-year holidays for a majority of the world,
the voting period MUST NOT start and MUST NOT end in the period between
December, 17th 00:00 UTC and January, 10th 00:00 UTC.

After the voting period has started, including after the vote closed and the RFC is
either accepted or declined, there MUST NOT be any further major or minor
changes to the RFC text and making editorial changes SHOULD be avoided for the
avoidance of doubt. The voting details (such as the voting period or interpretation
of secondary votes) MUST NOT be changed after the vote opened.

The voting period MAY be canceled within the first 2 days (48 hours) in case
of severe issues with the RFC. Canceling a vote is treated as a Major change thus
triggers a new cooldown period. The title of all voting widgets MUST be
changed to invalidate any votes that have been cast (e.g. by adding the suffix “(Restart)”).

=======
Errata
=======

If issues with an accepted RFC are noticed during implementation, an errata
section explaining the necessary changes SHOULD be added.

Should the necessary changes significantly impact the design, it MAY be
appropriate to start a follow-up discussion thread, or possibly a follow-up RFC.
At minimum, author(s) SHOULD send a notification message to the original
discussion thread describing the change.

If there is dispute as to whether a post-vote change requires a follow-up
discussion of its own, an RFC and vote of its own, or neither, the final
decision rests with the Release Managers.

This section has been amended by:

-  `Abolish Short Votes RFC <https://wiki.php.net/rfc/abolish-short-votes>`_.

*******************
 Required Majority
*******************

All votes in an RFC MUST have an "Abstain" option, which is treated identically
to not casting a vote in terms of calculating results, but is used as a signal
that eligible voters explicitly decline to vote one way or the other on a
question rather than simply not having noticed the RFC.

The primary vote of an RFC, determining overall acceptance of the proposal, MUST
be a clearly phrased binary question with the voting options "Yes", "No", and
"Abstain". The primary vote SHOULD be phrased "Implement $feature as outlined in
the RFC?" to avoid ambiguity. For a primary vote to be accepted a 2/3 majority
of "Yes" votes is required. This means that the number of "Yes" votes must be
greater than or equal to the number of "No" votes multiplied by two.

As an example, an RFC with 8 "Yes", 4 "No", and 9 "Abstain" votes is accepted,
as the number of "Yes" votes is twice the number of "No" votes and "Abstain"
votes do not take part in the calculation. An RFC with 5 "Yes", 3 "No", and 4
"Abstain" votes is not accepted.

Additionally, an RFC MAY have secondary votes, which are used to decide
implementation details. The result of secondary votes is void unless the
corresponding primary vote is accepted. Secondary votes MAY have more than two
voting options and MAY be decided by plurality (meaning that the voting option
with the most votes wins). For secondary votes with two voting options the RFC
author MAY decide on a higher threshold (up to a 2/3 majority) for an individual
option. Secondary votes with more than two voting options MAY also be decided
using the "Single transferable vote" voting system. The voting system used,
necessary threshold(s), and tie-breakers MUST be defined at the start of the
voting period.

As an example, a secondary vote using a plurality and having 5 "Foo", 4 "Bar", 8
"Baz", and 9 "Abstain" votes decided on the "Baz" result, since it has the most
number of votes excluding the "Abstain" option. It is not necessary to reach 50%
of the votes ("simple majority").

For procedural reasons, multiple related proposals MAY be combined into one RFC,
in which case there MAY be multiple primary votes. Combining multiple proposals
into one RFC MUST NOT be used to turn a primary vote into a secondary vote.

This section has been amended by:

-  `Abolish Narrow Margins RFC
   <https://wiki.php.net/rfc/abolish-narrow-margins>`_.

*********************************
 Resurrecting Rejected Proposals
*********************************

In order to save valuable time, it will not be allowed to bring up a rejected
proposal up for another vote, unless one of the following happens:

-  6 months pass from the time of the previous vote, **OR**

-  The author(s) make substantial changes to the proposal. While it's impossible
   to put clear definitions on what constitutes 'substantial' changes, they
   should be material enough so that they'll significantly affect the outcome of
   another vote.

**************
 Who Can Vote
**************

There's no way around this 'small' issue. Changes made to the PHP language will
affect millions of people, and theoretically, each and every one of them should
have a say in what we do. For obvious reasons, though, this isn't a practical
approach.

The proposal here is for two audiences to participate in the voting process:

-  People with php.net VCS accounts that have contributed code to PHP

-  Representatives from the PHP community, that will be chosen by those with
   php.net VCS accounts

   -  Lead developers of PHP based projects (frameworks, cms, tools, etc.)
   -  regular participant of internals discussions

**************
 RFC Proposer
**************

-  Proposers vote with +1 on their own RFC per default if they are allowed to
   vote
