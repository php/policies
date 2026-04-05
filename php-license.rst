#################
 The PHP License
#################

.. IMPORTANT::

   This is a meta document discussing the PHP license. For the actual PHP
   license, see `PHP Licensing`_.

On April 4, 2026, the PHP project adopted the `PHP License Update RFC`_, which
published new versions of the PHP License and the Zend Engine License, both
based on the `Modified BSD License`_ (SPDX: ``BSD-3-Clause``).

*********
 Changes
*********

The PHP Group invoked clause 5 of the PHP License, version 3.01, to publish the
PHP License, version 4. Zend Technologies invoked clause 4 of the Zend Engine
License, version 2.00, to publish the Zend Engine License, version 3. Both
organizations provided formal correspondence consenting to these changes.

The PHP project, the PHP Group, and Zend Technologies have deprecated the PHP
License and the Zend Engine License to decrease `license proliferation`_. Use of
these licenses for new projects is discouraged. The Modified BSD License (or
another compatible license) is recommended instead.

*****************
 Impact on Users
*****************

The rights granted to users under the PHP License, version 3.01, and the Zend
Engine License, version 2.00, do not change under the new license versions.

Maintainers of software licensed under the PHP License, version 3.01, may
relicense under PHP License, version 4, by exercising the upgrade clause in that
license. When doing so, use the SPDX identifier ``BSD-3-Clause`` rather than the
name "PHP License, version 4."

******************************
 Copyright and License Header
******************************

New source code files contributed to the PHP project should include the
following header block. See also the php-src CONTRIBUTING_ document.

.. code::

   /*
     +----------------------------------------------------------------------+
     | Copyright © The PHP Group and Contributors.                          |
     +----------------------------------------------------------------------+
     | This source file is subject to the Modified BSD License that is      |
     | bundled with this package in the file LICENSE, and is available      |
     | through the World Wide Web at <https://www.php.net/license/>.        |
     |                                                                      |
     | SPDX-License-Identifier: BSD-3-Clause                                |
     +----------------------------------------------------------------------+
     | Author:                                                              |
     +----------------------------------------------------------------------+
   */

***********
 Resources
***********

-  `PHP License Update RFC`_
-  `PHP License version 4`_
-  `PHP Group consent correspondence`_
-  `Zend Technologies consent letter`_

.. _contributing: https://github.com/ramsey/php-src/blob/master/CONTRIBUTING.md

.. _license proliferation: https://en.wikipedia.org/wiki/License_proliferation

.. _modified bsd license: https://opensource.org/license/bsd-3-clause

.. _php group consent correspondence: php-license/php-group-consent.pdf

.. _php license update rfc: https://wiki.php.net/rfc/php_license_update

.. _php license version 4: php-license/php-license-v4.txt

.. _php licensing: https://www.php.net/license/

.. _zend technologies consent letter: php-license/zend-technologies-consent.pdf
