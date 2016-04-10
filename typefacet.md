TypeFacet Autokern
==================

Charles M. Chen's [Autokern](http://charlesmchen.github.io/typefacet/topics/autokern/index.html) is a command-line Python tool released as
part of Chen's *TypeFacet* software collection.  It reads in UFO font
files and takes a set of user-supplied arguments, then outputs a
modified UFO file with adjusted side-bearings and, optionally, kerning
values.



Arguments
---------

### Basic operation

`--ufo-src-path` *foo.ufo* Sets the font file to be processed.

`--ufo-dst-path` *bar.ufo* Designates the name of the modified output
file to create.

`--log-path` *logs* Designates where output logs should be written.


### Common tunable settings
	
`--min-distance-ems` Sets a minimum allowable distance between the
contours of adjacent glyphs.

`--max-distance-ems` Sets the maximum distance allowed between any two glyphs. 


`--intrusion-tolerance-ems` Sets the maximum amount to which glyphs can "intrude" into the spacing between them. 

`--max-x-extrema-overlap-ems`

`--precision-ems` Sets the numeric precision to use for calculations.
Smaller values are more CPU intensive.


### Glyph selection

`--sample-texts`

`--kern-samples-only`

`--glyph-pairs-to-kern`

`--glyphs-to-kern`

`--glyphs-to-ignore`


### Additional tunable settings

`--do-not-modify-side-bearings` Tells Autokern to preserve the font's
original side bearings.

`--allow-negative-side-bearings` Tells Autokern to permit side
bearings to take on negative values.

`--kerning-threshold-ems` *N* Tells Autokern to discard any kerning
values less than N.

`--max-kerning-pairs` *N* Tells Autokern to only output the N largest
kerning values and discard the rest. 

`--x-extrema-overlap-scaling`

`--tracking-ems` *N* (mentioned in the documentation as `--tracking`)
Tells Autokern to add a constant N value to all kerning values.

`--ignore-x-extrema-overlap-outside-ascender`  Tells Autokern to
ignore x-extrema overlaps that occur below the baseline or above the
ascender.


### Glyph selection by category

`--glyph-categories-to-ignore`

`--max-x-extrema-overlap-ems-per-category`

`--max-distance-ems-per-category`

`--min-distance-ems-per-category`

`--intrusion-tolerance-ems-per-category`

`--tracking-ems-per-category`


### Additional logging options

`--log-basic-pairs` Tells Autokern to log the "basic" set of glyph
pairs, for use proofreading or troubleshooting.

`--write-kerning-pair-logs` Tells Autokern to log every kerning-pair combination.

`--disparity-log-count` Tells Autokern to log which kerning pairs were
changed by the greatest amount.



Usage
-----

Chen advises users to run the Autorkern tool several times, employing
a different subset of the arguments for each run.  First, he suggests
running with `--min-distance-ems` and `--max-distance-ems` on a pair
of glyphs such as "Tt", "TT", or "rf".
