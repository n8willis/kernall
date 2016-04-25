TypeFacet Autokern
==================

Charles M. Chen's [Autokern](http://charlesmchen.github.io/typefacet/topics/autokern/index.html) is a command-line Python tool released as
part of Chen's *TypeFacet* software collection.  It reads in UFO font
files and takes a set of user-supplied arguments, then outputs a
modified UFO file with kerning values and, optionally, adjusted side-bearings.

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
`min-distance-ems` parameter to some non-zero value.  Selecting the
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
and "maximum advance" values for the kerning pair.

Next, the `max-distance` profiles are adjusted to determine the
"intruding advance", which is the distance adjustment that results in the
most equally balanced "intrusion" amount for the two glyphs&mdash;that
is, each glyph intrudes by a close-to-equal amount, without exceeding the
intrusion tolerance parameter.

The intruding advance is found via 
binary search on the interval [0, int(ceiling(2.0 *
max(pair_intrusion_tolerance, pair_max_distance)))].  At each step,
the algorithm takes the horizontal distance between the facade profiles at
several y-axis values, looking for collisions between the profiles.
If a collision is detected, the next iteration moves to the "far" side
of the remaining search interval.

The final kern is determined by summing the intruding advance (or the
"minimum advance" value, if that is greater than the intruding
advance), any `tracking-ems` value provided as a parameter, the
`x-extrema-overlap-scaling` parameter, and the greater of the
`x-extrema-overlap` and `max-x-extrema-overlap` parameters.

The facade profiles used in the collision-detection and intrusion
steps are of reduced precision (in comparion to the font's internal
point system); the precision used is derived from the `precision-ems`
parameter. 

The algorithm can also be tweaked with the
`ignore-x-extrema-overlap-outside-ascender` parameter, which
limits the spacing-adjustment process to measurements within the x-height.

Analysis
--------

Bluntly speaking, Autokern makes "common sense" kerning calculations
based on what it assumes to be a properly letterspaced input font.
Which is to say that it attempts to make unobtrusive changes.

As far as the critical "intruding advance" step is concerned, the
algorithm measures the horizontal distance between the two glyphs at a
number of y-axis sample heights, but the samples also take three
specific conditions into account:

- Large contiguous gaps at the top of bottom are discarded; this
  removes the effect (for example) of the left ascender in the pair
  "hh".

- Large gaps in the middle of the height samples are de-emphasized by
  replacing them with the maximum protrusion value.  This removes
  undue impact from the open bowl in "c".

- Sample rows that exist solely because of the glyph-inflation process
  are discarded.  This essentially chops the profiles off at the
  original glyph's vertical extrema.

Together with the `pair-intrusion-tolerance` parameter, these conditions
restrict the intrusion-advance search to commonly accepted rules about
Latin typefaces.  That said, more specific rules might produce more
pleasing results.  As implemented, the rules are somewhat ad-hoc.  The
amount of "large contiguous gap" that triggers the "hh condition is
hard-coded to `pair_max_distance` * 0.5.  Depending on the typeface,
that might trigger false positives for (say) "L" or"T".

Several of the other conditions in the intruding-advance step are
similarly hard-coded.  It is an open question whether these metrics
produce the best results.

At a higher level, the glyph-inflation process used to create the
facade profiles might bear closer examination as well.  It "inflates"
glyphs by a fixed amount, both horizontally and vertically, in an
attempt to define a "bubble" into which adjacent glyphs should not
intrude.  But the fixed-radius inflation may not correspond well to
how glyphs (particularly those with dense or complex contours) behave.

Finally, the usage of the Autokern tool itself requires the user to
employ multiple, manual steps.  Much of the functionality could be
broken out into a reusable library to automate some of the
parameter-determining stages or to work interactively.

The manual determination of the parameters (particularly
`max-x-extrema-overlap-ems` and `intrusion-tolerance-ems`) is a
crucial input to the final results.  In a sense, since these
parameters are not automatically determined for a given input
typeface, the final output can only be considered partially automated.
