Frank Blokland's LetterModel method of spacing
==============================================

[LetterModel](http://www.lettermodel.org/) is spacing system described
by calligrapher and type designer Frank E. Blokland, resulting from
his doctoral research into historic type design and manufacturing.

Part of Blokland's central thesis is that Rennaissance punches were
cut in alignment with a grid system; between any two particular
typefaces, the number of units in the grid might vary, but, within a
single face, stems, counters, extenders, and sidebearings were aligned
to grid coordinates.

At his research blog, Blokland [describes]
(http://www.lettermodel.org/wordpress/?p=316) how the grid-based
approach can be applied to typefaces designed without a grid in mind
(or, in practical terms, typefaces designed on the fine-scale
coordinate grids inherent in TrueType or PostScript curves).

First, a
grid should be superimposed on the "n" glyph, with the number of units
adjusted so that both stems are aligned on veritcal grid
lines.

Second, the side bearings are set so that each bearing is half
the width of the counter inside the "n." From there, the side bearing
for the other glyphs can be computed algebraically.

For his example,
Blokland applies a 36-unit grid over a normally-proportioned Roman
face, and provides a chart listing the left- and right-sidebearings
for the full uppercase and lowercase basic Latin alphabet, plus the
period and comma.

The example results in left- and right-sidebearings
of 6 for the "n." Naturally, the relative proportions of all the
remaining bearings can be computed from that. So it is not strictly
necessary to space the "n" first. From a practical standpoint, the
cadence system is more complete than Tracy's method (which omitted
several letters), and it does not begin with an "optical fitting" step
for the starting glyph ("n" for the cadence method, as opposed to "n"
and "o" for the Tracy method).

Interestingly enough, the automatic
bearings chosen by the cadence method are derived from half the width
of the "n", which is identical to the sidebearings prescribed by
Frutiger's approach.

Thus, the cadence method essentially combines
Tracy and Frutiger's methods in a single approach.

The main limitation
is the method makes assumptions about the proportions and shapes of
the glyphs&mdash;namely, that they adhere to typical Rennaissance
forms. 
