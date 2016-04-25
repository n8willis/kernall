TypeFacet Autokern
==================

Charles M. Chen's [Autokern](http://charlesmchen.github.io/typefacet/topics/autokern/index.html) is a command-line Python tool released as
part of Chen's *TypeFacet* software collection.  It reads in UFO font
files and takes a set of user-supplied arguments, then outputs a
modified UFO file with adjusted side-bearings and, optionally, kerning
values.

Usage
-----

Autokern is run from the command line and the advised usage is to
execute multiple runs.  First, one should do a set of test runs on
small glyph sets to determine the values of font-wide parameters.
Then one can run Autokern on the entire font.

###Determining parameters

First, one runs Autokern with (essentially) all zeros; this sets the
`min-distance-ems`, `max-distance-ems`, `max-x-extrema-overlap-ems`
and `intrusion-tolerance-ems` parameters of the font to 0.  After this
step, one can inspect the output UFO file to note which glyph pairs
may be problematic.

Second, one runs Autokern again (on the same input UFO) to set the
`min-distance-ems1` parameter to some non-zero value.  Selecting the
appropriate value is up to the user based on trial runs and inspecting
the results.  The parameter is meant to reflect the minimum spacing
between two glyphs that come as close as possible to touching.  For
example, the pairs "TT", "vv", or "rf".  During this run,
`max-distance-ems` is also set to the same value, although it will
change later. 

Third, one runs Autokern again, this time to set the
`max-distance-ems` parameter.  Again the correct value is up to the
user to determine by inspection; it is meant to be the maximum space
allowed between two glyphs.  For Latin, the example pairs recommended
are "NN" and "||".  For serif faces, `max-distance-ems` is meant to
reflect the distance between stems.

Fourth, one runs Autokern to set the `intrusion-tolerance-ems`
parameter, which defines the maximum amount that glyphs can "intrude"
into the space between them.  The examples indicate that
such intrusion amounts to the distance that an extrema point can be
kerned into *unkerned* space of the sidebearings between a kerning
pair.  Furthermore, regardless of what the `intrusion-tolerance-ems`
setting is, no pair of glyphs will be kerned closer than
`min-distance-ems`, preventing collisions.  The example pairs
recommended are "AA" and "OO".

Fifth, one runs Autokern to set the `max-x-extrema-overlap-ems`
parameter.  This parameter sets the amount of (non-colliding) overlap
allowed between the extrema of a kerning pair.  For example, the
inner extrema of the classic "AV" and "VA" pairs are likely to overlap
each other horizontally, even though the contours do not touch.

###Kerning an entire font

After the parameter-setting tests described above, Autokern can be run
on an entire font.  The `precision-ems` parameter sets the smallest
step size that Autokern will use when making adjustments.  Selecting
too small of a value will result in long run times.

There are several other [arguments](typefacet-arguments.md) that one
can make use of at this stage for better control of the output.  In
particular, arguments can be used to limit kerning adjustments to a
specific [class](http://charlesmchen.github.io/typefacet/topics/autokern/glyph_categories.html) of glyphs, so that different rules can be applied to
different scripts, cases, and glyph types.  Autokern can also produce
helpful log files, including HTML output that may be easier to work
with than flat numeric data.


Algorithm
---------

The Autokern algorithm depends heavily on the parameters detemined in
the preceding steps.

For each kerning pair, two "facade profiles" are constructed for each
glyph: one pair by "inflating" each glyph a distance of
`min-distance-ems` and one pair by inflating each glyph a distance of
`max-distance-ems`.

The `min-distance` profiles are moved together until they touch, as are
the `max-distance` profiles.  This determines the "minimum advance"
and "maximum advance" for the kerning pair.

Next, the `max-distance` profiles are adjusted to determine the
"intruding advance", which is distance adjustment that results in the
most equally balanced "intrusion" amount for the two glyphs&mdash;that
is, each glyph intrudes by a close-to-equal amount, within the
intrusion tolerance parameter.  The intrusion advance is found by
binary search on the interval [0, int(ceiling(2.0 * max(pair_intrusion_tolerance, pair_max_distance)))].

The final kern is determined by summing the intruding advance (or the
minimum advance parameter, if it is greater than the intruding
advance), any pair-tracking value provided, the
`x-extrema-overlap-scaling` parameter, and the greater of the
`x-extrema-overlap` or `max-x-extrema-overlap` parameters.

The facade profiles used in the collision-detection and intrusion
steps are of reduced precision (in comparion to the font's internal
point system); the precision used is derived from the `precision-ems`
parameter. 

Analysis
--------

Bluntly speaking, Autokern makes "common sense" kerning calculations
based on what it assumes to be a properly letterspaced input font.
Which is to say that it attempts to make unobtrusive changes.
