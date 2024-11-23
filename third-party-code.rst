########################
 Third Party Code Usage
########################

**************
 Introduction
**************

The PHP project may leverage code written by others, of which the PHP ecosystem
has an ample supply. However, it also wants to avoid giving the appearance of
endorsing or recommending any particular tool over other equally-capable
competitors, even if unintentionally. This document provides a heuristic and
process for addressing that balance.

*************
 Definitions
*************

**PHP tooling**
   Refers to the code behind the PHP.net website, the documentation generator
   project PhD, the PHP wiki, and other similar systems. In general, “PHP code
   run by PHP.net.”

**Documentation**
   Refers to objective information about PHP, the PHP language, the PHP standard
   library, and PHP ecosystem hosted on PHP.net. This may include reference
   material, tutorials, FAQs, and similar.

**Marketing material**
   Refers to content on PHP.net or similar sites intended to promote or
   evangelize PHP the language or ecosystem.

**Libraries**
   Refers to existing third party code packages or tools, either C extensions or
   PHP code, maintained by someone other than the PHP Internals team. It also
   includes command line utilities used primarily by a developer. It may also
   refer to non-profit PHP ecosystem organizations, such as the PHP Foundation
   or PHP-FIG.

**Web Application**
   Refers to a “full” web framework that provides end-to-end web application
   capabilities, or an installable complete application. It does not refer to
   command line utilities used primarily by developers building applications.

**Approved license**
   Refers to a license `approved by the Free Software Foundation as Free
   Software <https://www.gnu.org/licenses/license-list.en.html>`_, and that is
   inbound compatible with GPLv3.

*********************
 Approval Heuristics
*********************

PHP Tooling
===========

PHP tooling MAY make use of third party libraries, provided that the library
meets all of the “Inclusion” criteria, and does not meet any of the “Exclusion”
criteria.

Inclusion criteria
------------------

#. The library must have a stable >= 1.0 release, and have had one for at least
   a year. (This is to ensure it has longevity.)
#. The library provides targeted, necessary functionality.
#. The library is a recognized de facto standard, or one of a small number of de
   facto standards, in its problem space.
#. The library is available under an Approved License.

Exclusion criteria
------------------

#. The library is a Web Application
#. The library is not available under an Approved License.
#. The library has shown no meaningful activity for one year prior to its first
   inclusion.

PHP tooling maintainers MAY use their judgement to determine if a library meets
the above criteria, but SHOULD be conservative in their interpretation of
whether or not a library satisfies the necessary criteria.

Explicitly approved libraries
-----------------------------

The following libraries have been explicitly approved by RFC vote.

-  Composer
-  Xdebug
-  phpunit/phpunit
-  phpstan/phpstan
-  vimeo/psalm
-  michelf/php-markdown
-  phpmailer/phpmailer
-  squizlabs/php_codesniffer
-  friendsofphp/php-cs-fixer
-  symfony/dotenv
-  symfony/console
-  fzaninotto/faker
-  erusev/parsedown
-  amenadiel/jpgraph
-  Any library or PSR published by the PHP-FIG

Explicitly rejected libraries
-----------------------------

None

PHP Documentation
=================

Documentation MAY reference and link to third party libraries, provided that the
library meets all of the “Inclusion” criteria, and does not meet any of the
“Exclusion” criteria. Additionally, the language used to refer to the library
must also follow the criteria below.

Inclusion criteria
------------------

#. The library must have a stable >= 1.0 release, and have had one for at least
   a year.

#. The library provides a use that is commonly needed by many types of projects,
   making it of broad interest to the PHP ecosystem.

#. The library is a recognized de facto standard, or one of a small number of de
   facto standards, in its problem space. If there are a small number of de
   facto standard libraries, then all should be listed and given equal weight.

#. The library is available under an Approved License.

#. The language used to describe the library does not imply that the PHP Project
   is involved in or specifically recommends the library over some other.

Exclusion criteria
------------------

#. The library is one of many (more than ~4) viable options in its problem
   space, even if it is the most common of those many options.
#. The library is a Web Application.
#. The library is not available under an Approved License.
#. The library has shown no meaningful activity for one year prior to its first
   mention.
#. The library is not of broad interest to the PHP ecosystem.

PHP tooling maintainers MAY use their judgement to determine if a library meets
the above criteria, but SHOULD be conservative in their interpretation of
whether or not a library satisfies the necessary criteria.

Explicitly approved libraries
-----------------------------

The following libraries have been explicitly approved by RFC vote.

-  Composer
-  Xdebug
-  phpunit/phpunit
-  phpstan/phpstan
-  vimeo/psalm
-  squizlabs/php_codesniffer
-  friendsofphp/php-cs-fixer
-  Any library or PSR published by the PHP-FIG

Explicitly rejected libraries
-----------------------------

None

Marketing Material
==================

Marketing material MAY reference and link to third party libraries, provided
that the library meets all of the “Inclusion” criteria, and does not meet any of
the “Exclusion” criteria. Additionally, the language used to refer to the
library must also follow the criteria below.

Inclusion criteria
------------------

#. The library must have a stable >= 1.0 release, and have had one for at least
   a year.

#. The library provides a use that is commonly needed by many types of projects,
   making it of *significant interest to the PHP ecosystem*.

#. The library is a recognized de facto standard, or one of a small number of de
   facto standards, in its problem space. If there are a small number of de
   facto standard libraries, then all should be listed and given equal weight.

#. The library MAY be a Web Application, provided its mention clearly does not
   specifically endorse the Application. If many options exist in a space that
   bears mention, the most common should be given equal exposure.

#. The library is available under an Approved License.

#. The language used to describe the library does not imply that the PHP Project
   is involved in or specifically recommends the library over some other.

Exclusion criteria
------------------

#. The library is not available under an Approved License.
#. The library has shown no meaningful activity for one year prior to its first
   mention.
#. The library is not of broad interest to the PHP ecosystem.

PHP marketing material maintainers MAY use their judgement to determine if a
library meets the above criteria, but SHOULD be conservative in their
interpretation of whether or not a library satisfies the necessary criteria.

Explicitly approved libraries
-----------------------------

The following libraries have been explicitly approved by RFC vote.

-  Composer
-  Xdebug
-  phpunit/phpunit
-  phpstan/phpstan
-  vimeo/psalm
-  squizlabs/php_codesniffer
-  friendsofphp/php-cs-fixer
-  Any library or PSR published by the PHP-FIG

Explicitly rejected libraries
-----------------------------

None

*********************
 Conflict Resolution
*********************

Should there be a reasonable dispute as to whether a given library satisfies the
criteria above, an RFC may be posted to explicitly approve the library for one
or more of the above cases. The RFC MUST have a 2/3 vote threshold to approve
the library. If the library is rejected, it may be revisited after six months,
like any other RFC.

Additionally, a library that does not satisfy the above criteria MAY be granted
an exception by RFC vote. The RFC MUST acknowledge the reasons the library does
not meet the above criteria and why it is necessary for the PHP project to make
use of or reference it anyway. The RFC MUST have a 2/3 vote threshold to approve
the library.

*********************
 Approved Exceptions
*********************

PHP Tooling
===========

-  Dokuwiki
