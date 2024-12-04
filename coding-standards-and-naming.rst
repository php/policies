####################################
 Coding Standards and Naming Policy
####################################

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be
interpreted as described in `RFC 2119
<https://datatracker.ietf.org/doc/html/rfc2119>`_.

**************
 Symbol Names
**************

Acronyms
========

Abbreviations and acronyms as well as initialisms SHOULD be avoided wherever
possible.

Abbreviations, acronyms, and initialisms MUST be treated like regular words,
thus they should be written with an uppercase first character, followed by
lowercase characters.

Diverging from this policy is NOT RECOMMENDED, but it is allowed to keep
internal consistency within a single extension, if the name follows an
established, language-agnostic standard, or for other reasons, if those reasons
are properly justified and voted on as part of the RFC process.

Methods
=======

Method names SHOULD follow the studlyCaps (also referred to as bumpy case or
camel caps) naming convention, with care taken to minimize the letter count. The
initial letter of the name is lowercase, and each letter that starts a new word
is capitalized.

Good method names:

-  ``connect()``
-  ``getData()``
-  ``buildSomeWidget()``
-  ``performHttpRequest()``

Bad method names:

-  ``get_Data()``
-  ``buildsomewidget()``
-  ``getI()``
-  ``performHTTPRequest()``

Classes
=======

Existing user-level class names are NOT RECOMMENDED to be changed. Although it
would be possible (class names are case-insensitive).

New class names MUST be descriptive nouns in PascalCase and as short as
possible. Each word in the class name MUST start with a capital letter, without
underscore delimiters. The class name MUST be prefixed with the name of the
"parent set" (e.g. the name of the extension) if no namespaces are used.

Good class names:

-  ``Curl``
-  ``CurlResponse``
-  ``HttpStatusCode``
-  ``Url``
-  ``BtreeMap`` (B-tree Map)
-  ``UserId`` (User Identifier)
-  ``Char`` (Character)
-  ``Intl`` (Internationalization)
-  ``Ssl\Certificate``
-  ``Ssl\Crl`` (Certificate Revocation List)
-  ``Ssl\CrlUrl``

Bad class names:

-  ``curl``
-  ``curl_response``
-  ``HTTPStatusCode``
-  ``URL``
-  ``BTreeMap``
-  ``UserID`` (User Identifier)
-  ``CHAR``
-  ``INTL``
-  ``SSL\Certificate``
-  ``SSL\CRL``
-  ``SSL\CRLURL``

************
 Namespaces
************

PHP Extension Classification
============================

All symbols (classes, functions, constants) provided by PHP are part of an
extension. Extensions can be classified into three categories:

-  Required extensions (including ``Core`` and ``standard``). These extensions
   are always present, and PHP cannot be built without them.

-  Bundled extensions (including ``ctype`` and ``mbstring``). These extensions
   are part of the php-src distribution, but PHP can be built without them.
   Bundled extensions can be either enabled or disabled by default.

-  3rd-party extensions (including ``apcu`` and ``igbinary``). These extensions
   are not part of the php-src distribution, and either available through PECL,
   or on GitHub.

Extensions may move between these three categories over time. ``hash`` and
``json`` moved from "bundled" to "required", in PHP 7.4 and 8.0 respectively.
``sodium`` and ``ffi`` moved from 3rd-party to bundled. ``xmlrpc`` and ``wddx``
moved from bundled to 3rd-party.

Core, Standard, Spl
===================

Symbols MUST NOT be namespaced under the ``Core``, ``Standard`` or ``Spl``
namespaces. Instead, these extensions should be considered as a collection of
different components (``str_*``, ``password_*``), and SHOULD be namespaced
according to these component names.

If a component gets introduced it MAY use a namespace. For example, if a new
component ``vector`` is introduced, it MUST consist of functions all starting
with ``vector_*`` (such as ``vector_multiply()``), OR they MUST all be
namespaced functions under the ``Vector`` namespace, such as
``Vector\multiply()``.

Bundled Extensions
==================

Bundled PHP extensions SHOULD use namespaces, subject to the guidelines laid out
in the following:

-  Extensions MUST NOT use a vendor namespace.
-  The top-level namespace MUST match the extension name (apart from casing).
-  Namespace names MUST follow ``CamelCase``.
-  All symbols defined in the extension SHOULD be part of the extension's
   top-level namespace or a sub-namespace.

This policy allows the use of namespaces, and provides basic guidelines for
their use. It does not propose to migrate already existing non-namespaced
symbols to use namespaces.

Examples
--------

If we were to introduce ``openssl`` as a new namespaced extension, here is how
the symbol names could change in line with these guidelines:

-  ``OpenSSLCertificate`` becomes ``OpenSSL\Certificate``
-  ``openssl_dh_compute_key()`` becomes ``OpenSSL\dh_compute_key()``
-  ``X509_PURPOSE_SSL_CLIENT`` becomes ``OpenSSL\X509_PURPOSE_SSL_CLIENT``

The above guidelines recommend against the global ``FFI`` class used by the
``ffi`` extension. Using ``FFI\FFI`` would be preferred.

Existing Non-Namespaced Symbols and Consistency
===============================================

When adding new symbols to existing extensions it is RECOMMENDED to be
consistent with existing symbols, rather than to follow the namespacing
guidelines.

For example, the ``array_is_list()`` function added in PHP 8.1 MUST indeed be
called ``array_is_list()`` and MUST NOT have been introduced as
``Array\is_list()`` or similar. Unless and until existing ``array_*()``
functions are aliased under an ``Array\*`` namespace, new additions MUST
continue to be of the form ``array_*()`` to maintain horizontal consistency.

This is a somewhat loose guideline, and applies more strongly to functions than
classes. In particular, when new object-oriented elements are introduced into an
extension that has historically been procedural, these MAY be namespaced. For
example, if ``OpenSSLCertificate`` had only been introduced in PHP 8.1, it could
have been named ``OpenSSL\Certificate``.

For the Core, Standard, and Spl extensions, the previous considerations on
component subdivision apply. The fact that string and array functions are not
namespaced does not preclude new namespaced components in these extensions.

Namespace Collisions
====================

As a matter of courtesy, top-level namespaces used by extensions SHOULD avoid
collisions with existing, commonly used open-source libraries or extensions (or
happen with the agreement of the parties involved). This document does not try
to provide a hard guideline on what constitutes a sufficiently important
library. The application of common sense is recommended.

**************
 Related RFCs
**************

-  From: `Class Naming RFC <https://wiki.php.net/rfc/class-naming>`_
-  From: `Casing of acronyms in class and method names RFC
   <https://wiki.php.net/rfc/class-naming-acronyms>`_
-  From `Namespaces in Bundled Extensions RFC
   <https://wiki.php.net/rfc/namespaces_in_bundled_extensions>`_.
