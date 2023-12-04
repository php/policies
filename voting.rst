Voting on PHP features
======================

Introduction
------------

This document describes the procedure to propose an idea for adoption by the
PHP community and decide if the community accepts or rejects the idea.

Proposal Initiation
-------------------

Proposal is formally initiated by creating an RFC on PHP wiki and announcing it
on the list. If the proposal is a repeated discussion of an existing RFC, with
or without modification, it still should be announced on the list for
discussion. 

The announcement will be done in a way that's easy to flag & follow, e.g. - by
``[RFC]`` in the subject line followed by the title of the RFC.

The proposal should be initiated by one of its authors. If the proposal is a
repeated one, re-proposed by somebody else, the proposer should discuss it with
the original author, if possible, and add himself to the RFC author list before
proposing it.

If the proposer is not a member of php.net and thus can not create RFCs on the
wiki, they should recruit one of the members for help or request membership. 

Discussion Period
-----------------

There'd be a minimum of 2 weeks between when an RFC that touches the language
is brought up on this list and when it's voted on is required. Other RFCs might
use a smaller timeframe, but it should be at least a week. The effective date
will not be when the RFC was published on the PHP wiki - but when it was
announced on ``internals@lists.php.net``, by the author, with the intention of
voting on it. This period can be extended when circumstances warrant it - such
as major conferences, key people being busy, force major events, or when
discussion merits it - but should never be less than minimal time. 

This does not preclude discussion on the merits on any idea or proposal on the
list without formally submitting it as a proposal, but the discussion time is
measured only since the formal discussion announcement as described above. 

Voting
------

This section has been amended by the `Abolish Short Votes RFC
<https://wiki.php.net/rfc/abolish-short-votes>`_.

The author decides when it's time to move ahead and call a vote on the RFC.  If
the author feels that there's still healthy discussion going on, they can
decide not to move ahead to request a vote after the minimal period, but extend
it as needed.  On the other hand, if they feel that the discussion is being
derailed - they can always move ahead to a vote as long as the minimum
discussion time elapsed.

The vote is announced on the mailing list in a separate thread by sending an
email with the subject ``[VOTE]``. It should reference the RFCs being voted on
and if there are different options discussed, explain these options. It should
also contain the URL of the page where the vote is taking place. 

Votes should be open for two weeks at minimum, at the authors discretion this
may be extended, for example during holiday periods. 

A valid voting period must be declared when voting is started and must not be
changed during the vote.

Required Majority
-----------------

This section has been amended by the `Abolish Narrow Margins RFC
<https://wiki.php.net/rfc/abolish-narrow-margins>`_.

The primary vote of an RFC, determining overall acceptance of the proposal, may
only have two voting options and requires a 2/3 majority. This means that the
number of Yes votes must be greater than or equal to the number of No votes
multiplied by two.

Additionally, an RFC may have secondary votes, which are used to decide
implementation details. Such votes may have more than two voting options and
may be decided by simple plurality. This means that the voting option with the
most votes wins. If there are multiple options with the most number of votes,
it is left at the discretion of the RFC author to choose one of them.

For procedural reasons, multiple RFCs may be combined into one, in which case
there may be multiple primary votes. Combining multiple RFCs into one does not
allow turning a primary vote into a secondary vote.


Resurrecting Rejected Proposals
-------------------------------

In order to save valuable time, it will not be allowed to bring up a rejected
proposal up for another vote, unless one of the following happens:

  * 6 months pass from the time of the previous vote, OR
  * The author(s) make substantial changes to the proposal. While it's
    impossible to put clear definitions on what constitutes 'substantial'
    changes, they should be material enough so that they'll significantly
    affect the outcome of another vote.

Who Can Vote
------------

There's no way around this 'small' issue.  Changes made to the PHP language
will affect millions of people, and theoretically, each and every one of them
should have a say in what we do.  For obvious reasons, though, this isn't a
practical approach.

The proposal here is for two audiences to participate in the voting process:

  * People with php.net VCS accounts that have contributed code to PHP
  * Representatives from the PHP community, that will be chosen by those with
    php.net VCS accounts

    * Lead developers of PHP based projects (frameworks, cms, tools, etc.)
    * regular participant of internals discussions

RFC Proposer
------------

  * Proposers vote with +1 on their own RFC per default if they are allowed to vote
