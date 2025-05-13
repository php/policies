##########
 Policies
##########

This repository contains a list of policies that the PHP Project has adopted
through its RFC process to govern releases, voting, and naming guidelines.

It contains the following items:

-  `Release Process <release-process.rst>`_: When releases are made, how they
   are named, our policy on version numbers, and the process on making releases.

-  `Feature Proposals (RFCs) <feature-proposals.rst>`_: How to propose new
   features to PHP.

-  `Coding Standards <coding-standards-and-naming.rst>`_: How to name new
   classes, methods, extensions, and functions.

-  `Security Classification <security-classification.rst>`_: What we consider as
   security issues, their severity, and how to report issues.

-  `Security Policies and Process <security-policies.rst>`_: Policies and
   process on how and when to update the `security.txt
   <https://www.php.net/.well-known/security.txt>`_ file on https://www.php.net.

-  `Third-Party code <third-party-code.rst>`_: The circumstances under which the
   PHP project will use PHP code written by third parties in the ecosystem.

***********************
 Requirements Notation
***********************

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in `BCP 14
<https://www.rfc-editor.org/bcp/bcp14.txt>`_ [`RFC2119
<https://datatracker.ietf.org/doc/html/rfc2119>`_] [`RFC8174
<https://datatracker.ietf.org/doc/html/rfc8174>`_] when, and only when, they
appear in all capitals, as shown here.

************
 Formatting
************

The files in this documentation are formatted using the `rstfmt
<https://github.com/dzhu/rstfmt>`_ tool, which you can install with:

.. code::

   python3 -m venv ~/install/rstfmt
   ~/install/rstfmt/bin/pip3 install rstfmt
   sudo ln -s ~/install/rstfmt/bin/rstfmt /usr/local/bin/rstfmt

Please run the tool before submitting a pull request:

.. code::

   rstfmt -w 80 *.rst
