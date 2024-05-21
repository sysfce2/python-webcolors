.. _colors:


An overview of colors on the web
================================

Colors on the web are typically specified in `the sRGB color space`_, where
each color is made up of a red component, a green component and a blue
component. This maps to the red, green and blue components of the pixels on a
computer display, and to the three sets of cone cells in an average
trichromatic human eye, whose peak responses are (roughly) to the wavelengths
of light associated with red, green and blue.

On the web, sRGB colors are specified in formats which describe the color as a
24-bit integer, where the first 8 bits provide the red value, the second 8 bits
the green value and the final 8 bits the blue value. This gives a total space
of 256 × 256 × 256 or 16,777,216 unique colors, though due to differences in
display technology not all of these colors may be clearly distinguishable on
any given physical display.


HTML 4
------

HTML 4 defined `two ways to specify sRGB colors`_:

* The character ``#`` followed by three pairs of hexadecimal digits, specifying
  values for red, green and blue components in that order; for example,
  ``#0099cc``.

* A set of predefined color names which correspond to specific hexadecimal
  values; for example, ``blue``. HTML 4 defines sixteen such colors.


CSS1
----

In `its description of color units`_, CSS1 added three new ways to specify sRGB
colors:

* The character ``#`` followed by three hexadecimal digits, which is expanded
  into three hexadecimal pairs by repeating each digit; thus ``#09c`` is
  equivalent to ``#0099cc``.

* The string ``rgb``, followed by parentheses, between which are three base-10
  integers in the range 0..255, which are taken to be the values of the red,
  green and blue components in that order; for example, ``rgb(0, 153, 204)``.

* The same as above, except using percentages instead of numeric values; for
  example, ``rgb(0%, 60%, 80%)``.

CSS1 also suggested a set of sixteen color names. These names were identical to
the set defined in HTML 4, but CSS1 did not provide definitions of their values
and stated that they were taken from "the Windows VGA palette".


CSS2
----

In its `section on colors`_, CSS2 allowed the same methods of specifying colors
as CSS1, and defined and provided values for sixteen named colors, identical to
the set found in HTML 4.

CSS2 also specified `a list of names of system colors`_. These had no fixed
color values, but would take on values from the operating system or other user
interface, and allowed elements to be styled using the same colors as the
surrounding user interface. These names are deprecated as of CSS3.

The CSS2.1 revision did not add any new methods of specifying sRGB colors, but
did define `one additional named color`_: ``orange``.


CSS3
----

`The CSS3 color module`_ adds one new way to specify colors:

* A hue-saturation-lightness triplet (HSL), using the construct ``hsl()``.

CSS3 also adds support for variable opacity of colors, by allowing the
specification of alpha-channel information through the ``rgba()`` and
``hsla()`` constructs. These are used similarly to the ``rgb()`` and ``hsl()``
constructs, except a fourth value is supplied indicating the level of opacity
from ``0.0`` (completely transparent) to ``1.0`` (completely opaque). Though
not technically a color, the keyword ``transparent`` is also made available in
lieu of a color value, and corresponds to ``rgba(0,0,0,0)``.

CSS3 also defines a new set of 147 color names. This set is taken directly from
`the named colors defined for SVG (Scalable Vector Graphics)`_ markup, and is a
superset of the named colors defined in CSS2.1.


HTML5
-----

HTML5 originally existed in two forms: a living document maintained by WHATWG,
and a W3C Recommendation. The W3C Recommendation has now been "retired" in
favor of the WHATWG living standard.

HTML5 does not introduce any new methods of specifying colors, but does
simplify the description of colors and introduce useful terminology.

* A set of three 8-bit numbers representing the red, blue and green components
  of an sRGB color is termed a "simple color".

* A seven-character string which begins with the character ``#``, followed by
  six ASCII hex digits (i.e., ``A-Fa-f0-9``), representing the red, green and
  blue components of an sRGB color, is a "valid simple color".

* A valid simple color expressed with only lowercase ASCII hex digits (i.e.,
  ``a-f0-9``) is a "valid lowercase simple color".

HTML5 provides three algorithms related to colors:

1. An algorithm for parsing simple color values, which works on any string that
   is a valid simple color as defined above.

2. An algorithm for serializing simple color values, which will always produce
   a valid lowercase simple color.

3. A legacy color-parsing algorithm, which will yield a simple color from a
   variety of inputs, including inputs which are valid simple colors, inputs
   which are valid for formats from other standards, and certain types of
   "junk" inputs which were common in real-world documents.

The HTML5 legacy parsing algorithm does not support the non-color keyword
``transparent`` from CSS3 and will produce an error for that input. It also
does not recognize the CSS2 "system color" keywords; it will convert each such
keyword to a simple color, consistently, but in a way which does not follow
CSS2's definitions of these keywords (which itself was system- and
configuration-dependent).

The implementations in this module are based on the definitions and algorithms
of `the HTML5 specification's section on colors`_.

.. _the sRGB color space: http://www.w3.org/Graphics/Color/sRGB
.. _two ways to specify sRGB colors: http://www.w3.org/TR/html401/types.html#h-6.5
.. _its description of color units: http://www.w3.org/TR/CSS1/#color-units
.. _section on colors: http://www.w3.org/TR/CSS2/syndata.html#color-units
.. _a list of names of system colors: http://www.w3.org/TR/CSS2/ui.html#system-colors
.. _one additional named color: https://www.w3.org/TR/CSS21/changes.html#q21.2
.. _The CSS3 color module: http://www.w3.org/TR/css3-color/
.. _the named colors defined for SVG (Scalable Vector Graphics): http://www.w3.org/TR/SVG11/types.html#ColorKeywords
.. _the HTML5 specification's section on colors: https://html.spec.whatwg.org/multipage/common-microsyntaxes.html#colours


.. _support:

What this module supports
-------------------------

The ``webcolors`` module supports the following methods of specifying sRGB
colors, and conversions between them:

* Six-digit hexadecimal

* Three-digit hexadecimal

* Integer ``rgb()`` triplet

* Percentage ``rgb()`` triplet

* The defined named colors of HTML 4, CSS2, CSS2.1, and CSS3

The ``webcolors`` module **does not support**:

* The CSS1 named colors, which did not have defined values

* The CSS2 system colors, which did not have fixed values

* The ``transparent`` keyword, which denotes an effective lack of
  color

* Opacity/alpha-channel information specified via the ``rgba()``
  construct

* Colors specified in the HSL color space, via ``hsl()`` or `hsla()`
  constructs

If you need to convert between sRGB-specified colors and HSL-specified colors,
or colors specified via other means, consult the :mod:`colorsys` module in the
Python standard library, which can perform conversions amongst several common
color systems.
