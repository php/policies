###############################
 Security Policies and Process
###############################

.. IMPORTANT::

   This is a meta document discussing PHP security policies and processes. For
   the actual PHP security policy, see the PHP `Vulnerability Disclosure Policy
   <https://github.com/php/policies/blob/main/security-classification.rst>`_
   document.

***************************
 PHP.net security.txt file
***************************

PHP.net includes a `security.txt
<https://www.php.net/.well-known/security.txt>`_ file that complements the
`Vulnerability Disclosure Policy
<https://github.com/php/policies/blob/main/security-classification.rst>`_,
aiding security vulnerability disclosure. This file implements the standard
defined in `RFC 9116 <https://www.rfc-editor.org/rfc/rfc9116>`_, and more
information is available at <https://securitytxt.org>.

RFC 9116 requires an ``Expires`` field in ``security.txt``, and its
recommendation is for the ``Expires`` field to be less than a year in the
future. This provides security researchers with confidence they are using our
most up-to-date reporting policies. To facilitate yearly updates to the
``Expires`` field and ensure freshness of the information in ``security.txt``,
the PHP release managers `update the Expires field as part of the X.Y.0 GA
release
<https://github.com/php/php-src/blob/master/docs/release-process.md#preparing-for-the-initial-stable-version-php-xy0>`_.

From time-to-time, we may update ``security.txt`` with new information, outside
of the yearly changes to the ``Expires`` field.

Making changes to security.txt
==============================

All changes to ``security.txt`` must be signed by a PHP release manager for a
`currently supported version of PHP
<https://www.php.net/supported-versions.php>`_ (at the time of the changes).
Release managers are the most logical choice for signing this file, since we
already `publish their PGP keys <https://www.php.net/gpg-keys.php>`_.

To make changes to ``security.txt``:

#. Go to your local clone of `web-php <https://github.com/php/web-php>`_:

   .. code::

      cd /path/to/web-php/.well-known

#. Remove the PGP signature that wraps the body of ``security.txt``:

   .. code::

      gpg --decrypt --output security.txt security.txt

   .. NOTE::

      To "decrypt" ``security.txt``, you will need the public key of the release
      manager who last signed it in your GPG keychain.

#. Make and save your changes to this file, e.g., update the ``Expires``
   timestamp.

   There should be a "Signed by" comment in the file that looks similar to this:

   .. code::

      # Signed by Ben Ramsey <ramsey@php.net> on 2023-09-28.

   Update this line with your name, the email address associated with the key
   you're using to sign the file, and the current date.

#. Sign your changes:

   .. code::

      gpg --clearsign --local-user YOU@php.net --output security.txt.asc security.txt

   .. WARNING::

      You cannot use ``--output`` to output the signature to the same file as
      the input file or ``gpg`` will result in a signature wrapped around empty
      content.

#. Last, replace ``security.txt`` with ``security.txt.asc`` and commit your
   changes:

   .. code::

      mv security.txt.asc security.txt
      git commit security.txt

   .. NOTE::

      You may verify the signature with the following command:

      .. code::

         gpg --verify security.txt
