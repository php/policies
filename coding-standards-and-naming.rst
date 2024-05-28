==================================
Coding Standards and Naming Policy
==================================

Classes
=======

From: `Class Naming RFC <https://wiki.php.net/rfc/class-naming>`_

**Editor’s note: Parts of this RFC have been superseded by the “Casing of acronyms in class and method names” section**

The PHP coding standard does not cover how class names should be written. This
leads to friction within the userland community that is now largely following
the `standard recommendation PSR-1 <http://www.php-fig.org/psr/psr-1/>`_.

Extending our current coding standard to cover edge cases about abbreviations
and acronyms/initialisms would resolve any future discussion.

Proposal
--------

Extend the coding standard to explicitly specify how abbreviations and
acronyms/initialisms are to be handled when writing user-level class names.
The current rule is::

    Classes should be given descriptive names. Avoid using abbreviations where
    possible. Each word in the class name should start with a capital letter,
    without underscore delimiters (CamelCaps starting with a capital letter).
    The class name should be prefixed with the name of the 'parent set' (e.g.
    the name of the extension)::

    Good:
    'Curl'
    'FooBar'

    Bad:
    'foobar'
    'foo_bar'

— `CODING_STANDARDS <https://github.com/php/php-src/blob/abac7e81dd7b2e851562c60377951da5a5a99e30/CODING_STANDARDS#L154-L166>`_.

While it is stated that abbreviations should be avoided, it is silent on what
to do if they are used; especially in the case of acronyms/initialisms. There
are essentially three choices possible now:

- **PascalCase except Acronyms/Initialisms** — which is how the majority of
  user-level class names are written, and it matches the approach of many
  other programming languages.
- **Always PascalCase** — which is basically what
  `PSR-1 <http://www.php-fig.org/psr/psr-1/>`_ defines, however, it would
  make most of the currently existing user-level class names invalid.
- **Do Nothing** — which of course automatically means that any approach is
  allowed, and the community discussions around this topic will continue.

**IMPORTANT!**: Regardless of the outcome of this RFC, existing user-level
class names are not required to be changed. Although it would be possible
(class names are case-insensitive). The reason why renaming is not proposed is
simple: this RFC would most probably fail because too many people are against
such purely cosmetic changes.

PascalCase except Acronyms/Initialisms
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Editor’s note: This section has been superseded by the “Casing of acronyms in class and method names” section**

Class names should be descriptive nouns in PascalCase and as short as
possible. Each word in the class name should start with a capital letter,
without underscore delimiters. The class name should be prefixed with the name
of the "parent set" (e.g. the name of the extension) if no namespaces are
used. Abbreviations and acronyms as well as initialisms should be avoided
wherever possible, unless they are much more widely used than the long form
(e.g. HTTP or URL). Abbreviations start with a capital letter followed by
lowercase letters, whereas acronyms and initialisms are written according to
their standard notation. Usage of acronyms and initialisms is not allowed if
they are not widely adopted and recognized as such.

Good:

- ``Curl``
- ``CurlResponse``
- ``HTTPStatusCode``
- ``URL``
- ``BTreeMap`` (B-tree Map)
- ``Id`` (Identifier)
- ``ID`` (Identity Document)
- ``Char`` (Character)
- ``Intl`` (Internationalization)
- ``Radar`` (Radio Detecting and Ranging)

Bad:

- ``curl``
- ``curl_response``
- ``HttpStatusCode``
- ``Url``
- ``BtreeMap``
- ``ID`` (Identifier)
- ``CHAR``
- ``INTL``
- ``RADAR`` (Radio Detecting and Ranging)

Casing of acronyms in class and method names
============================================

From: `Casing of acronyms in class and method names RFC <https://wiki.php.net/rfc/class-naming-acronyms>`_

The class naming policy should be updated to the following, with changes highlighted:

Method names follow the studlyCaps (also referred to as bumpy case or camel caps) naming convention, with care taken to minimize the letter count. The initial letter of the name is lowercase, and each letter that starts a new word is capitalized.

Class names should be descriptive nouns in PascalCase and as short as possible. Each word in the class name should start with a capital letter, without underscore delimiters. The class name should be prefixed with the name of the "parent set" (e.g. the name of the extension) if no namespaces are used.

Abbreviations and acronyms as well as initialisms should be avoided wherever possible, unless they are much more widely used than the long form (e.g. HTTP or URL).

.. raw:: html

   <s>Abbreviations start with a capital letter followed by lowercase letters, whereas acronyms and initialisms are written according to their standard notation.</s>

**Abbreviations, acronyms, and initialisms should be treated like regular words, thus they should be written with an uppercase first character, followed by lowercase characters.** 

.. raw:: html

   <s>Usage of acronyms and initialisms is not allowed if they are not widely adopted and recognized as such.</s>

**Diverging from this policy is allowed to keep internal consistency within a single extension, if the name follows an established, language-agnostic standard, or for other reasons, if those reasons are properly justified and voted on as part of the RFC process.**

Examples
--------

Good method names:

- ``connect()``
- ``getData()``
- ``buildSomeWidget()``
- ``performHttpRequest()``

Bad method names:

- ``get_Data()``
- ``buildsomewidget()``
- ``getI()``
- ``performHTTPRequest()``

Good class names:

- ``Curl``
- ``CurlResponse``
- ``HttpStatusCode``
- ``Url``
- ``BtreeMap`` (B-tree Map)
- ``UserId`` (User Identifier)
- ``Char`` (Character)
- ``Intl`` (Internationalization)
- ``Ssl\Certificate``
- ``Ssl\Crl`` (Certificate Revocation List)
- ``Ssl\CrlUrl``

Bad class names:

- ``curl``
- ``curl_response``
- ``HTTPStatusCode``
- ``URL``
- ``BTreeMap``
- ``UserID`` (User Identifier)
- ``CHAR``
- ``INTL``
- ``SSL\Certificate``
- ``SSL\CRL``
- ``SSL\CRLURL``

Namespaces in Extensions
========================

From `Namespaces in Bundled Extensions RFC
<https://wiki.php.net/rfc/namespaces_in_bundled_extensions>`_.

Classes and functions provided by bundled PHP extensions are currently all
located in the global namespace (with one exception). There is a strong
sentiment that future additions to PHP's standard library should make use of
namespaces, to the point that otherwise unrelated proposals increasingly
degenerate into namespace-related discussions. This question needs to be
resolved one way or another, to avoid reiterating it for every future addition
to the standard library.

PHP Extension Classification
----------------------------

All symbols (classes, functions, constants) provided by PHP are part of an
extension. Extensions can be classified into three categories:

- Required extensions (including Core and standard). These extensions are
  always present, and PHP cannot be built without them.
- Bundled extensions (including ctype and mbstring). These extensions are
  part of the php-src distribution, but PHP can be built without them.
  Bundled extensions can be either enabled or disabled by default.
- 3rd-party extensions (including apcu and igbinary). These extensions are
  not part of the php-src distribution, and either available through PECL,
  or simply on GitHub.

Extensions may move between these three categories over time. hash and json
recently moved from "bundled" to "required" (though I believe extensions never
move out of the "required" category). sodium and ffi moved from 3rd-party to
bundled. xmlrpc and wddx moved from bundled to 3rd-party.

Vendor Namespace
----------------

Most userland open-source libraries nowadays follow a namespace structure of
the form ``VendorNamespace\PackageNamespace\Symbol``, with all names being at
least two levels deep. PSR-4 itself only requires a top-level namespace and
permits symbols of the form ``TopLevelNamespace\Symbol``.

The concept of a vendor namespace is hard to reconcile with the extension
classification discussed in the previous section, as extensions may move
between different "vendors". It is educative to consider the issues that a
''PHP\Component\Symbol'' name structure would encounter, which was assumed by
many prior RFCs and discussions.

3rd-party extensions clearly cannot start out under a ''PHP'' namespace, as
they have no direct relation to, endorsement by, or oversight of the PHP
project. If all symbols in bundled extensions are to be prefixed by ''PHP'',
this would require a rename of all symbols when an extension moves from
3rd-party to bundled. While compatibility shims can somewhat mitigate this,
such a rename constitutes an unnecessary disruption to all existing users of
the extension, as well as any documentation relating to it.

Conversely, if a bundled extension is removed from PHP, the question arises
whether it should be moved out of the ''PHP'' namespace. Extensions are
typically unbundled from PHP if they are unmaintained. Retaining them under
the ''PHP'' namespace may create the mistaken impression that the PHP project
still maintains such extensions. Of course, changing the vendor prefix on
unbundling would once again disrupt any remaining users.

The `PHP Namespace Policy <https://wiki.php.net/rfc/php_namespace_policy>`_ RFC (declined) RFC sought to address
this by introducing two vendor namespaces for extensions: ''PHP'' and ''Ext''.
The latter may be used by all extensions, whether they be bundled or
3rd-party. The ''PHP'' namespace would only be eligible for bundled
functionality directly tied to PHP, such as built-in attributes, altough the
exact dividing line is unclear. Most symbols would be part of the ''Ext''
vendor namespace.

Existing practice
-----------------

PHP itself only bundles a single extension with namespaced symbols (ffi).
However, there are a number of 3rd-party extensions making use of namespaces.
For extensions present in phpstorm-stubs, the following list summarizes in
what way they utilize namespaces:

- ``ffi`` (bundled): Uses ``FFI`` namespace, e.g. ``FFI\CType``. Also uses ``FFI`` itself.
- ``aerospike``: Uses ``Aerospike`` namespace, e.g. ``Aerospike\Bytes``. Also uses ``Aerospike`` itself.
- ``cassandra``: Uses ``Cassandra`` namespace, e.g. ``Cassandra\Table``. Also uses ``Cassandra`` itself.
- ``couchbase``: Uses ``Couchbase`` namespace, e.g. ``Couchbase\Document``.
- ``crypto``: Uses ``Crypto`` namespace, e.g. ``Crypto\PBKDF2``.
- ``decimal``: Uses ``Decimal`` namespace, e.g. ``Decimal\Decimal``.
- ``ds``: Uses ``Ds`` namespace, e.g. ``Ds\Collection``.
- ``grpc``: Uses ``Grpc`` namespace, e.g. ``Grpc\Server``.
- ``http``: Uses ``http`` namespace, e.g. ``http\Client``.
- ``mongodb``: Uses ``MongoDB`` namespace, e.g. ``MongoDB\Driver\Manager``.
- ``mosquitto``: Uses ``Mosquitto`` namespace, e.g. ``Mosquitto\Client``.
- ``mysql_xdevapi``: Uses ``mysql_xdevapi`` namespace, e.g. ``mysql_xdevapi\Collection``.
- ``parallel``: Uses ``parallel`` namespace, e.g. ``parallel\Runtime``.
- ``parle``: Uses ``Parle`` namespace, e.g. ``Parle\Lexer``.
- ``pcov``: Uses ``pcov`` namespace, e.g. ``pcov\start()``.
- ``pq``: Uses ``pq`` namespace, e.g. ``pq\Connection``.
- ``rdkafka``: Uses ``RdKafka`` namespace, e.g. ``RdKafka\Producer``. Also uses ``RdKafka`` itself, and a handful of ``rd_kafka_*()`` functions.
- ``xlswriter``: Uses ``Vtiful\Kernel`` namespace, e.g. ``Vtiful\Kernel\Excel``.
- ``yaf``: Uses ``Yaf`` namespace, e.g. ``Yaf\Application``. Also supports aliases in the global namespace, e.g. ``Yaf_Application``.
- ``zstd``: Uses ``Zstd`` namespace, e.g. ``Zstd\compress()``. However, it also declares ``zstd_*()`` functions in the global namespace.

It is notable that with the exception of ``xlswriter``, none of these
extensions make use of a vendor namespace. They all use the package/extension
name as the top-level namespace. Some extensions additionally have a global
class that matches the extension name, e.g. the ffi extension uses both
``FFI`` and ``FFI\CType``.

Proposal
--------

This RFC proposes to explicitly allow and encourage the use of namespaces for
bundled PHP extensions, subject to the guidelines laid out in the following:

- Extensions should not use a vendor namespace.
- The top-level namespace should match the extension name (apart from
  casing).
- Namespace names should follow ``CamelCase``.
- All symbols defined in the extension should be part of the extension's
  top-level namespace or a sub-namespace.

Examples
~~~~~~~~

If we were to introduce ``openssl`` as a new namespaced extension, here is how
the symbol names could change in line with these guidelines:

- ``OpenSSLCertificate`` becomes ``OpenSSL\Certificate``
- ``openssl_dh_compute_key()`` becomes ``OpenSSL\dh_compute_key()``
- ``X509_PURPOSE_SSL_CLIENT`` becomes ``OpenSSL\X509_PURPOSE_SSL_CLIENT``

The above guidelines recommend against the global ``FFI`` class used by the
ffi extension. Using ``FFI\FFI`` would be preferred.

Core, standard, spl
~~~~~~~~~~~~~~~~~~~

PHP has three extensions that together form the core of the standard library.
The "Core" extension is part of the Zend Engine, and defines a relatively
small number of functions and classes. It contains core types like
``stdClass`` and ``Iterator``, as well as introspection functions like
``get_object_vars()``. The "standard" extension contains the majority of the
standard library functions, including ``array_*()`` and ``str_*()`` functions.
The "spl" extension was historically the "object-oriented" part of the
standard library, containing data-structures like ``ArrayObject``, exceptions
and iterators.

The distinction between these three extensions is somewhat murky from an
end-user perspective, and largely historical. Symbols have moved between these
extensions, e.g. the ``Iterator`` interface originated in spl, but now lives
in Core.

Because these extensions combine a lot of unrelated or only tangentially
related functionality, symbols should not be namespaced under the ``Core``,
``Standard`` or ``Spl`` namespaces. Instead, these extensions should be
considered as a collection of different components, and should be namespaced
according to these.

For example, ``str_contains()`` could become ``Str\contains()``, ``fopen()``
could become ``File\open()``, and ``password_hash()`` could become
``Password\hash()``. (These are non-normative examples, the RFC does not
propose using these specific namespaces.)

Existing non-namespaces symbols and consistency
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When adding new symbols to existing extensions, it is more important to be
consistent with existing symbols than to follow the namespacing guidelines.

For example, the ``array_is_list()`` function added in PHP 8.1 should indeed
be called ``array_is_list()`` and should not be introduced as
``Array\is_list()`` or similar. Unless and until existing ``array_*()``
functions are aliased under an ``Array\*`` namespace, new additions should
continue to be of the form ``array_*()`` to maintain horizontal consistency.

This is a somewhat loose guideline, and applies more strongly to functions
than classes. In particular, when new object-oriented elements are introduced
into an extension that has historically been procedural, these may be
namespaced. For example, if ``OpenSSLCertificate`` had only been introduced in
PHP 8.1, it should have been named ``OpenSSL\Certificate``.

For the Core/standard/spl extensions, the previous considerations on component
subdivision apply. The fact that string and array functions are not namespaced
does not preclude new namespaced components in these extensions.

Namespace collisions
~~~~~~~~~~~~~~~~~~~~

The disadvantage of not using a vendor namespace is that namespace collisions
are more likely. A mitigating factor is the pervasive use of vendor namespaces
in the userland ecosystem (in which case the collision would have to be
between a vendor namespace and a component namespace, which is less likely).

As a matter of courtesy, top-level namespaces used by extensions should avoid
collisions with existing, commonly used open-source libraries or extensions
(or happen with the agreement of the parties involved). This RFC does not try
to provide a hard guideline on what constitutes a sufficiently important
library. The application of common sense is recommended.

Future Scope
~~~~~~~~~~~~

This RFC only officially allows use of namespaces, and provides basic
guidelines for their use. However, it does not propose to migrate already
existing non-namespaced symbols to use namespaces. Such a migration should be
the subject of a separate RFC.
