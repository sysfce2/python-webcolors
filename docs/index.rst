webcolors |release|
===================

``webcolors`` is a module for working with and converting between the various
HTML/CSS color formats.

Support is included for normalizing and converting between the following
formats (RGB colorspace only; conversion to/from HSL can be handled by the
:mod:`colorsys` module in the Python standard library):

* Specification-defined color names

* Six-digit hexadecimal

* Three-digit hexadecimal

* Integer ``rgb()`` triplet

* Percentage ``rgb()`` triplet

For example:

.. code-block:: python

    >>> import webcolors
    >>> webcolors.hex_to_name("#daa520")
    'goldenrod'

Implementations are also provided for the HTML5 color parsing and serialization
algorithms. For example, parsing the infamous "chucknorris" string into an
``rgb()`` triplet:

.. code-block:: python

    >>> import webcolors
    >>> webcolors.html5_parse_legacy_color("chucknorris")
    HTML5SimpleColor(red=192, blue=0, green=0)


Documentation contents
----------------------

.. toctree::
   :caption: Getting started
   :maxdepth: 1

   install

.. toctree::
   :caption: Reference
   :maxdepth: 1

   colors
   conventions
   contents
   conformance

.. toctree::
   :caption: Other documentation
   :maxdepth: 1

   changelog
   faq

.. seealso::

  * `The sRGB color space <http://www.w3.org/Graphics/Color/sRGB>`_
  * `HTML 4: Colors <http://www.w3.org/TR/html401/types.html#h-6.5>`_
  * `CSS1: Color units <http://www.w3.org/TR/CSS1/#color-units>`_
  * `CSS2: Colors <http://www.w3.org/TR/CSS2/syndata.html#color-units>`_
  * `CSS3 color module <http://www.w3.org/TR/css3-color/>`_
  * `HTML5: Colors <https://html.spec.whatwg.org/multipage/common-microsyntaxes.html#colours>`_
