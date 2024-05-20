.. _changelog:


Changelog
=========

This document lists the changes in each release of ``webcolors``.


Version numbering
-----------------

This library currently tracks its version numbers using the ``YY.MM.MICRO``
form of `Calendar Versioning <https://calver.org>`_ ("CalVer"), in which the
first two components of the version number are the (two-digit) year and
(non-zero-padded) month of the release date, while the third component is an
incrementing value for releases occurring in that month. For example, the first
release issued in January 2025 would have a version number of 25.1.0; a
subsequent release in the same month would be 25.1.1; a release the following
month (February) would be 25.2.0.

The CalVer system was adopted for this library in 2024, and the first release
to use a CalVer version number was 24.5.0.


API stability and deprecations
------------------------------

The API stability/deprecation policy for this library is as follows:

* The supported stable public API of this library is the set of symbols which
  are exported by its ``__all__`` declaration and which are documented in this
  documentation. For classes exported there, the supported stable public API is
  the set of methods and attributes of those classes whose names do not begin
  with one or more underscore (``_``) characters and which are documented in
  this documentation.

* When a public API is to be removed, or undergo a backwards-incompatible
  change, it will emit a deprecation warning which serves as notice of the
  intended removal or change, and which will give a date -- which will always
  be at least in the next calendar year after the first release which emits the
  deprecation warning -- past which the removal or change may occur without
  further warning.

* Security fixes, and fixes for high-severity bugs (such as those which might
  cause unrecoverable crash or data loss), are not required to emit deprecation
  warnings, and may -- if needed -- impose backwards-incompatible change in any
  release. If this occurs, this changelog document will contain a note
  explaining why the usual deprecation process could not be followed for that
  case.

* This policy is in effect as of the adoption of CalVer versioning, with
  version 24.5.0 of this library.


Releases under CalVer
---------------------

Version 24.5.0
~~~~~~~~~~~~~~

*Not yet released*

* Supported Python versions are now 3.8, 3.9, 3.10, and 3.11.

* Running the unit tests no longer uses a third-party test runner; the
  standard-library ``unittest`` module's runner is used instead.

* Adopted `CalVer versioning <https://calver.org>`_.


Version 1.13, released 2023-??-??
---------------------------------

No bug fixes or new features.

Other changes
~~~~~~~~~~~~~

* Supported Python versions are now 3.7, 3.8, 3.9, 3.10, and 3.11

* The codebase was significantly reorganized and modernized. Public API is
  unchanged. Imports should continue to be directly from the top-level
  ``webcolors`` module; attempting to import from submodules is not supported.

* Now packaging declaratively via ``pyproject.toml`` with `PEP 517
  <https://peps.python.org/pep-0517/>`_ support from ``setuptools``.


Version 1.12, released 2022-05-25
---------------------------------

No bug fixes or new features.

Other changes
~~~~~~~~~~~~~

* Supported Python versions are now 3.7, 3.8, 3.9, and 3.10.


Version 1.11.1, released 2020-02-17
-----------------------------------

Bugs fixed
~~~~~~~~~~

* Corrected an error regarding supported Python versions in the README file.


Version 1.11, released 2020-02-17
---------------------------------

No bug fixes or new features.

Other changes
~~~~~~~~~~~~~

* Python 2 has reached the end of its support cycle from the Python core team;
  accordingly, Python 2 support is dropped. Supported Python versions are now
  3.5, 3.6, 3.7, and 3.8.


Version 1.10, released 2019-09-08
---------------------------------

No bug fixes or new features.

Other changes
~~~~~~~~~~~~~

* Similar to the change in version 1.9 which normalized conversions to named
  colors for ``gray``/``grey`` to always use the ``gray`` variant, the other
  named grays of CSS3 now normalize to the ``gray`` spelling. This affects the
  following colors: ``darkgray``/``darkgrey``,
  ``darkslategray``/``darkslategrey``, ``dimgray``/``dimgrey``,
  ``lightgray``/``lightgrey``, ``lightslategray``/``lightslategrey``,
  ``slategray``/``slategrey``.


Version 1.9.1, released 2019-06-07
----------------------------------

Bugs fixed
~~~~~~~~~~

* The ``__version__`` attribute of the installed webcolors module, although not
  documented or referenced anywhere, was accidentally not updated in the 1.9
  release. It has now been updated (and now indicates 1.9.1).


Version 1.9, released 2019-06-01
--------------------------------

No bug fixes.

New features
~~~~~~~~~~~~

* Added :ref:`a set of constants to use when referring to specifications that
  define color names <spec-constants>`.

Other changes
~~~~~~~~~~~~~

* When asked to provide a color name, using the CSS3/SVG set of names, for the
  hexadecimal value ``#808080``, the integer triplet ``rgb(128, 128, 128)``, or
  the percentage triplet ``rgb(50%, 50%, 50%)``, webcolors now always returns
  ``u'gray'``, never ``u'grey'``. Previously, the behavior could be
  inconsistent as it depended on the Python version in use; ``u'gray'`` was
  picked because it was the spelling variant used in HTML 4, CSS1, and CSS2.


Version 1.8.1, released 2018-02-12
----------------------------------

The 1.8.1 release is a repackaging of 1.8 to produce both source (.tar.gz) and
binary (.whl) package formats, following reports that the source-package-only
release of 1.8 was causing installation issues for some users. See `issue 6 in
the repository <https://github.com/ubernostrum/webcolors/issues/6>`_ for
details.


Version 1.8, released 2018-02-08
--------------------------------

No bug fixes.

New features
~~~~~~~~~~~~

* Added the :class:`~webcolors.IntegerRGB`,
  :class:`~webcolors.PercentRGB`, and
  :class:`~webcolors.HTML5SimpleColor` named tuples.

Other changes
~~~~~~~~~~~~~

* Drop support for Python 3.3 (Python core team no longer maintains 3.3).

* Mark support for Python 3.6.

* :ref:`The full verification tests <full-verification>` now run correctly on
  Python 3.


Version 1.7, released 2016-11-25
--------------------------------

No new features or bugfixes.

Other changes
~~~~~~~~~~~~~

* Drop support for Python 2.6 (Python core team no longer maintains 2.6).

* Mark support for Python 3.4.

* On Python 3, the use of :class:`str` for all functions which take string
  arguments is now mandatory. Attempted use of :class:`bytes` will raise an
  exception. On Python 2, use of bytestrings is still permitted.


Version 1.5.1, released 2015-11-23
----------------------------------

No new features.

Bug fixes
~~~~~~~~~

* Corrected multiple typos in documentation.



Version 1.5, released 2015-03-07
--------------------------------

No bug fixes.


New features
~~~~~~~~~~~~

* Python 3 support: webcolors now supports Python 3.3.

* Added :ref:`HTML5 color algorithms <html5-algorithms>`.

Other changes
~~~~~~~~~~~~~

* Packaging improvements.


Version 1.4, released 2012-02-10
--------------------------------

No new features.

Bugs fixed
~~~~~~~~~~

* Integer and percentage ``rgb()`` triplets now normalized in accordance with
  CSS clipping rules.

Other changes
~~~~~~~~~~~~~

* Packaging fixes.

* Preparatory work for Python 3 support.


Version 1.3.1, released 2009-10-24
----------------------------------

No new features or bugfixes.

Other changes
~~~~~~~~~~~~~

* Documentation expanded.

* Documentation now maintained using `Sphinx <http://www.sphinx-doc.org/>`_.


Version 1.3, released 2009-05-08
--------------------------------

No new features or bugfixes.

Other changes
~~~~~~~~~~~~~

* Documentation expanded.


Version 1.2, 2009-03-01
-----------------------

Bugs fixed:
~~~~~~~~~~~

* Corrected the download URL in the ``setup.py`` script.


Version 1.1, released 2008-12-19
--------------------------------

No new features or bugfixes.

Other changes
~~~~~~~~~~~~~

* Documentation expanded.


Version 1.0, released 2008-10-28
--------------------------------

Initial stable release of webcolors.
