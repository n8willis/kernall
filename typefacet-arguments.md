Autokern Arguments
==================

### Basic operation

`--ufo-src-path` *foo.ufo* Sets the font file to be processed.

`--ufo-dst-path` *bar.ufo* Designates the name of the modified output
file to create.

`--log-path` *logs* Designates where output logs should be written.


### Common tunable settings
	
`--min-distance-ems` Sets a minimum allowable distance between the
contours of adjacent glyphs.

`--max-distance-ems` Sets the maximum distance allowed between any two
glyphs in the typeface. 

`--intrusion-tolerance-ems` Sets the maximum amount to which a pair of
kerned glyphs can "intrude" into the spacing between them.  In
practice, this parameter corresponds roughly to the horizontal extent
of a pair of serifs.

`--max-x-extrema-overlap-ems` Sets the maximum amount to which glyphs' *extrema*
are allowed to overlap once kerned.  This does not allow contours to
intersect; rather, it is the maximum amount by which (for example) the
extrema of the glyphs in "VA" overlap.

`--precision-ems` Sets the numeric precision to use for calculations.
Smaller values are more CPU intensive.


### Glyph selection

`--sample-texts` "*AbCdEfXyZ*" Sets the glyphs to be examined.

`--kern-samples-only` Restricts output to kerning values and not side bearings.

`--glyph-pairs-to-kern` *A V T o A v* Sets pairs of glyphs to be kerned.

`--glyphs-to-kern` "*AaBbCcDd*" Sets a list of glyphs to be kerned;
all combinations will be processed.

`--glyphs-to-ignore` "*QqXxYyZz*" Sets a list of glyphs to skip.


### Additional tunable settings

`--do-not-modify-side-bearings` Tells Autokern to preserve the font's
original side bearings.

`--allow-negative-side-bearings` Tells Autokern to permit side
bearings to take on negative values.

`--kerning-threshold-ems` *N* Tells Autokern to discard any kerning
values less than N.

`--max-kerning-pairs` *N* Tells Autokern to only output the N largest
kerning values and discard the rest. 

`--x-extrema-overlap-scaling` *N* Sets a multiplier to be applied to
the `x-extrema-overlap-ems` values.  Can be used to in combination
with the glyph-selection arguments to scale the results for different
classes of glyphs (e.g., miniscules and majuscules).

`--tracking-ems` *N* (mentioned in the documentation as `--tracking`)
Tells Autokern to add a constant N value to all kerning values.

`--ignore-x-extrema-overlap-outside-ascender`  Tells Autokern to
ignore x-extrema overlaps that occur below the baseline or above the
ascender.


### Glyph selection by category

These settings allow the user to alter the Autokern run according to classes of
glyph.  Each class must be specified by a [Unicode
category](http://charlesmchen.github.io/typefacet/topics/autokern/glyph_categories.html).
For example, `Po` for "Punctuation, other" or "Lu" for "Letter,
uppercase."  Each of these arguments can take a space-separated list
of classes (followed, where necessary by numercic values).

`--glyph-categories-to-ignore` *Cc* *Cd* *[…]* Sets glyph classes to skip in this run.

`--max-x-extrema-overlap-ems-per-category` *Cc* *N* *Cd* *M*  *[…]* Sets the
`max-x-extrema-overlap-ems` parameter for a class or list of glyph classes.

`--max-distance-ems-per-category` *Cc* *N* *Cd* *M*  *[…]* Sets the
`max-distance-ems` parameter for a class or list of glyph classes.

`--min-distance-ems-per-category` *Cc* *N* *Cd* *M*  *[…]* Sets the
`max-x-distance-ems` parameter for a class or list of glyph classes.

`--intrusion-tolerance-ems-per-category` *Cc* *N* *Cd* *M*  *[…]* Sets the
`intrusion-tolerance-ems` parameter for a class or list of glyph classes.

`--tracking-ems-per-category` *Cc* *N* *Cd* *M*  *[…]* Sets the
`tracking-ems` parameter for a class or list of glyph classes.


### Additional logging options

`--log-basic-pairs` Tells Autokern to log the "basic" set of glyph
pairs, for use proofreading or troubleshooting.

`--write-kerning-pair-logs` Tells Autokern to log every kerning-pair combination.

`--disparity-log-count` Tells Autokern to log which kerning pairs were
changed by the greatest amount.

