####################################
 Coding Standards and Naming Policy
####################################

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in `BCP 14
<https://www.rfc-editor.org/bcp/bcp14.txt>`_ [`RFC2119
<https://datatracker.ietf.org/doc/html/rfc2119>`_] [`RFC8174
<https://datatracker.ietf.org/doc/html/rfc8174>`_] when, and only when, they
appear in all capitals, as shown here.

This policy lists standards that any programmer adding or changing code in PHP
should follow.

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

Functions
=========

Function names MUST be in lowercase, with words underscore delimited, with care
taken to minimize the letter count.

Good function names:

-  ``str_word_count``
-  ``array_key_exists``

Bad function names:

-  ``hw_GetObjectByQueryCollObj``
-  ``pg_setclientencoding``
-  ``jf_n_s_i``

If functions are part of a "parent set" of functions, that parent MUST be
included in the user function name, and should be clearly related to the parent
program or function family. This should be in the form of ``parent_*``:

A family of ``foo`` functions, for example:

Good names:

-  ``foo_select_bar``
-  ``foo_insert_baz``
-  ``foo_delete_baz``

Bad names:

-  ``fooselect_bar``
-  ``fooinsertbaz``
-  ``delete_foo_baz``

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

************************
 Implementation Details
************************

#. Document your code in source files and the manual. (tm)

#. PHP is implemented in C11.

   For instance, the optional fixed-width integers from ``stdint.h``
   (``int8_t``, ``int16_t``, ``int32_t``, ``int64_t`` and their unsigned
   counterparts) are supposed to be available.

#. Functions that are given pointers to resources SHOULD NOT free them, unless
   this is documented.

   For instance, ``function int mail(char *to, char *from)`` should NOT free
   ``to`` and/or ``from``.

   Exceptions:

   -  The function's designated behavior is freeing that resource. E.g.
      ``efree()``.

   -  The function is given a boolean argument, that controls whether or not the
      function may free its arguments (if ``true``, the function must free its
      arguments; if ``false``, it must not).

   -  Low-level parser routines, that are tightly integrated with the token
      cache and the bison code for minimum memory copying overhead.

#. Functions that are tightly integrated with other functions within the same
   module, and rely on each other's non-trivial behavior, MUST be documented as
   such and declared ``static``.

#. You SHOULD use definitions and macros whenever possible, so that constants
   have meaningful names and can be easily manipulated. Any use of a numeric
   constant to specify different behavior or actions SHOULD be done through a
   ``#define``.

#. When writing functions that deal with strings, you SHOULD use
   ``zend_string``, which holds the value and the length property of each
   string.

   Write your functions in such a way so that they'll take advantage of the
   length property by using ``ZSTR_LEN()``, both for efficiency, and in order
   for them to be binary-safe.

#. You SHOULD use the ``smart_str_*`` family of functions for string creation,
   instead of relying on the C-library versions, such as ``strncat()``.

#. You SHOULD use ``PHP_*`` macros in the PHP source, and ``ZEND_*`` macros in
   the Zend part of the source. Although the ``PHP_*`` macros are mostly aliased
   to the ``ZEND_*`` macros it gives a better understanding on what kind of
   macro you're calling.

#. You MUST NOT define functions that are not available. For instance, if a
   library is missing a function, do not define the PHP version of the function,
   and do not raise a run-time error about the function not existing. End users
   should use ``function_exists()`` to test for the existence of a function.

#. You SHOULD use ``emalloc()``, ``efree()``, ``estrdup()``, instead of their
   standard C library counterparts. These functions implement an internal
   "safety-net" mechanism that ensures the deallocation of any unfreed memory at
   the end of a request. They also provide useful allocation and overflow
   information while running in debug mode.

   In almost all cases, memory returned to the engine must be allocated using
   ``emalloc()``.

   The use of ``malloc()`` SHOULD be limited to cases where a third-party
   library may need to control or free the memory, or when the memory in
   question needs to survive between multiple requests.

#. The return type of "is" or "has" style functions SHOULD be ``bool`` which
   return a "yes"/"no" answer. `zend_result` is an appropriate return value for
   functions that perform some operation that may succeed or fail.

Variable Names
==============

Variable names MUST be meaningful. One letter variable names SHOULD be avoided,
except for places where the variable has no real meaning or a trivial meaning
(e.g. ``for (i=0; i<100; i++) ...``).

Variable names MUST be in lowercase. Use underscores to separate between words.

Internal Function Naming Conventions
====================================

The main module source file MUST be named ``modulename.c``.

Header files that are used by other sources must be named ``php_modulename.h``.

Functions that are part of the external API MUST be named
``php_modulename_function()`` to avoid symbol collision. They MUST be in
lowercase, with words underscore delimited. Exposed API MUST be defined in
``php_modulename.h``:

.. code::

   PHPAPI char *php_session_create_id(PS_CREATE_SID_ARGS);

Unexposed module function MUST be ``static`` and MUST NOT be defined in
`php_modulename.h`:

.. code::

   static int php_session_destroy()

Syntax and indentation
======================

You SHOULD Use K&R-style. When you write code that goes into the core of PHP or
one of its standard modules, please maintain the K&R style.

Be generous with whitespace and braces. Keep one empty line between the variable
declaration section and the statements in a block, as well as between logical
statement groups in a block. Maintain at least one empty line between two
functions. Always prefer:

.. code::

   if (foo) {
       bar;
   }

to:

.. code::

   if(foo)bar;

You MUST use the tab character when indenting. A tab is expected to represent
four spaces. It is important to maintain consistency in indentation so that
definitions, comments, and control structures line up correctly.

Preprocessor statements (``#if`` and such) MUST start at column one. To indent
preprocessor directives you should put the ``#`` at the beginning of a line,
followed by any number of spaces.

The length of constant string literals SHOULD be calculated via ``strlen()``
instead of using ``sizeof()-1`` as it is clearer and any modern compiler will
optimize it away. Legacy usages of the latter style exists within the codebase
but SHOULD NOT be refactored, unless larger refactoring around that code is
taking place.

Testing
=======

Extensions SHOULD be well tested using ``*.phpt`` tests. Read more at
`qa.php.net documentation <https://qa.php.net/write-test.php>`_.

Experimental Functions
======================

New extensions MUST start out as third-party extensions, or in an experimental
branch, until an RFC is passed to add them to the core distribution.

Aliases & Legacy Documentation
==============================

You may also have some deprecated aliases with close to duplicate names, for
example, ``somedb_select_result`` and ``somedb_selectresult``. For documentation
purposes, these will only be documented by the most current name, with the
aliases listed in the documentation for the parent function. For ease of
reference, user-functions with completely different names, that alias to the
same function (such as ``highlight_file`` and ``show_source``), will be
separately documented.

Backwards compatible functions and names SHOULD be maintained as long as the
code can be reasonably be kept as part of the codebase. See the `README in the
PHP documentation repository
<https://github.com/php/doc-base/blob/master/README.md>`_ for more information
on documentation.

**************
 Related RFCs
**************

-  From: `Class Naming RFC <https://wiki.php.net/rfc/class-naming>`_
-  From: `Casing of acronyms in class and method names RFC
   <https://wiki.php.net/rfc/class-naming-acronyms>`_
-  From `Namespaces in Bundled Extensions RFC
   <https://wiki.php.net/rfc/namespaces_in_bundled_extensions>`_.
